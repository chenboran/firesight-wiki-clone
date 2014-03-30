_FireSight_ _calcOffset_ compares the pipeline image with a baseline template image and 
computes the XY offset between the two images. It is implemented using 
[OpenCV matchTemplate](http://docs.opencv.org/modules/imgproc/doc/object_detection.html?highlight=matchtemplate#matchtemplate)
but the implementation is unique to _FireSight_. The XY offsets computed by _calcOffset_ are helpful
in many CNC scenarios:

* backlash detection
* mechanical limit stop calibration
* camera resolution calibration
* semi-closed loop operation

The output image of the [calcOffset.json](https://github.com/firepick1/FireSight/blob/master/json/calcOffset.json) 
pipeline has two stages. The first stage is _calcOffset_. The second stage draws the green lines:

<img src="https://github.com/firepick1/FireSight/blob/master/img/calcOffset-1.png?raw=true">

A typical pipeline output image is shown above. The inner green rectangle is the region of interest used for _matchTemplate_.
The outer green rectangle is the matchable area computed from the _xtol_ and _ytol_ parameters (see below).
The upper left inset is the correlation output from _matchTemplate_&mdash;white pixels indicate high correlation. 

* **channels** JSON array of integers that specifies the image channels used for comparison. 
The default is `[]`, which specifies a grayscale conversion. Use `[0,1,2]` for a BGR comparison. 
Use `[2]` for a red channel comparison.
* **minval** Minimum matching correlation value (0 is no match, 1 is perfect match). The default is `0.7`.
* **template** File path of baseline template image
* **xtol** X-axis +/- image comparison tolerance. Default is `32` pixels. 
Smaller values will result in higher accuracy. Larger tolerances are less accurate but let you detect larger offsets.
* **ytol** Y-axis +/- image comparison tolerance. Default is `32` pixels. 
Smaller values will result in higher accuracy. Larger tolerances are less accurate but let you detect larger offsets.

###### Special considerations
**Perspective matters.**
The XY offsets returned only apply to the Z plane of the images. Images that are nearer/farther will 
result in different XY offsets for the identical linear motion of camera and objective. For example, if the camera/objective 
Z-distance is increased by as little as a centimeter, the XY offsets will change by several pixels.

**Resolution** of _calcOffset_ is 1 pixel. For the Raspberry Pi camera lens in macro mode, 
this is easily 100 microns or less. A future implementation of _calcOffset_ may use interpolation to obtain sub-pixel
resolution.

#### Model
The _calcOffset_ JSON model consists of:

**channels** is a JSON object with a key/value pair for each matched channel. 
The JSON object for each matched channel is a JSON object with: 

* x offset (`dx`) 
* y offset (`dy`)
* highest matched correlation value (`match`)

If you specify grayscale conversion (i.e., channels=[])for color images, the matched channel will be "0". 
If you specify multiple channels (e.g., channels=[0,1,2]), individual XY offsets are computed for each channel as shown above.
Normally, one channel is enough, specifying more channels is slower since matchTemplate is executed for each channel.

**rects** is a JSON array with two rectangles. The smaller rectangle is the region of interest (ROI) used by _matchTemplate_.
The larger rectangle is ROI extended by the X and Y tolerances. The rectangles are constant, but
may prove useful as a visual guide in the output image. In the examples, these rects are displayed with a green border.
<pre>
{
  "channels":{
    "0":{ "dx":14, "dy":0, "match":"0.978238" },
    "1":{ "dx":14, "dy":0, "match":"0.984594" },
    "2":{ "dx":14, "dy":0, "match":"0.976005" }
  },
  "rects":[
    { "x":400, "y":100, "width":736, "height":136, "angle":0 },
    { "x":400, "y":100, "width":800, "height":200, "angle":0 }
  ]
}
</pre>

### Example 1: Horizontal 1mm offset [pipeline](https://github.com/firepick1/FireSight/blob/master/json/calcOffset.json)
<pre>firesight -i img/headcam1.jpg -p json/calcOffset.json -o target/calcOffset-1.png -Dtemplate=img/headcam0.jpg</pre>
> Pixel:11.3ms

The image below is the _calcOffset_ output of comparing a baseline image with one that was taken 1mm to the right of
the baseline image:

<img src="https://github.com/firepick1/FireSight/blob/master/img/calcOffset-1.png?raw=true">

### Example 2: Horizontal 0mm offset [pipeline](https://github.com/firepick1/FireSight/blob/master/json/calcOffset.json)
<pre>firesight -i img/headcam0a.jpg -p json/calcOffset.json -o target/calcOffset-1.png -Dtemplate=img/headcam0.jpg</pre>
> Pixel:11.3ms

The image below is the _calcOffset_ output of comparing a baseline image with one that was taken 
after the camera was moved and returned to the "same position". Note that the X and Y offset are non-zero,
which indicates that the camera detected a ~100 micron translation error due to backlash, micro-step loss, etc.

<img src="https://github.com/firepick1/FireSight/blob/master/img/calcOffset-0a.png?raw=true">

<pre>
{
  "channels":{
    "0":{ "dx":1, "dy":1, "match":"0.994095" }
  },
  "rects":[
    { "x":400, "y":100, "width":736, "height":136, "angle":0 },
    { "x":400, "y":100, "width":800, "height":200, "angle":0 }
  ]
}
</pre>
