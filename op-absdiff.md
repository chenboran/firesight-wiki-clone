_FireSight_ wrapper for [OpenCV absdiff](http://opencv.jp/opencv-2svn_org/cpp/core_operations_on_arrays.html#cv-absdiff), which takes the per-channel absolute difference of two images. _FireSight_ stage compares specified image with current pipeline image and changes output to the absolute difference of the two.

* **path** Path to second image

#### Model
The _absdiff_ pipeline operation by itself does not add anything to the data model, but it may be convenient to append a [calcHist](op calcHist) stage to the pipeline in order to add a histogram to the model. In the example shown below, the histogram indicates that the 200x800 images compared are identical because the _absdiff_ output is 0 for all pixels.
<pre>{
  "FireSight":{
    "version":"0.8.5",
    "url":"https://github.com/firepick1/FireSight"
  },
  "s1":{},
  "s2":{
    "hist":{
      "0":[
        160000,
        160000,
        160000
      ]
    }
  }
}</pre>

#### Example: Not all green [pipeline](https://github.com/firepick1/FireSight/blob/master/json/absdiff.json)
<pre>firesight -i img/pcb.jpg -p json/absdiff.json -Dimg=img/mog2.jpg -o target/absdiff.png</pre>
> Pixel:4ms

The pipeline image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

The comparison image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true">

Note that the absolute difference of the two is not all green even though the only "difference" between the two images is that one has green text. <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

