The _FireSight_ _calcOffset_ computes the XY offset of a given pipeline image from a given baseline template image. 
It is implemented using [OpenCV matchTemplate](http://docs.opencv.org/modules/imgproc/doc/object_detection.html?highlight=matchtemplate#matchtemplate)
but the code for _calcOffset_ is unique to _FireSight_

<img src="https://github.com/firepick1/FireSight/blob/master/img/calcOffset-1.png?raw=true">

* **channels** JSON array of integers that specifies the image channels used for comparison. The default is `[]`, which uses a grayscale conversion. Specify `[0,1,2]` for a BGR comparison; `[2] for a red channel comparison, etc.
* **minval** Minimum matching value (0 is no match, 1 is perfect match). The default is `0.7`.
* **template** Path to baseline template image
* **xtol** X-axis +/- image comparison tolerance. Default is `32` pixels. Smaller values will result in higher accuracy. Larger values will let you detect larger offsets.
* **ytol** Y-axis +/- image comparison tolerance. Default is `32` pixels. Smaller values will result in higher accuracy. Larger values will let you detect larger offsets.

#### Model
The [calcOffset.json](https://github.com/firepick1/FireSight/blob/master/json/calcOffset.json) pipeline has two stages. The first stage computes the _absdiff_. The second stage adds the [histogram](op calcHist) of the _absdiff_ image to the model. For example, if we compare identical 200x800 images, we would expect to see a histogram showing that all pixels are 0:

<pre>
{
  "FireSight":{
    "version":"0.9.1",
    "url":"https://github.com/firepick1/FireSight"
  },
  "calcOffset-stage":{
    "channels":{
      "0":{
        "dx":14,
        "dy":0,
        "match":"0.984573"
      }
    },
    "rects":[
      {
        "x":400,
        "y":100,
        "width":736,
        "height":136,
        "angle":0
      },
      {
        "x":400,
        "y":100,
        "width":800,
        "height":200,
        "angle":0
      }
    ]
  },
  "s2":{}
}
</pre>

#### Example: Not all green [pipeline](https://github.com/firepick1/FireSight/blob/master/json/absdiff.json)
<pre>firesight -i img/pcb.jpg -p json/absdiff.json -Dimg=img/mog2.jpg -o target/absdiff.png</pre>
> Pixel:4ms

The pipeline image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

The comparison image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true">

Note that the absolute difference of the two is not all green even though the only "difference" between the two images is that one has green text. <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">
