The _FireSight_ wrapper for [OpenCV threshold](http://docs.opencv.org/modules/imgproc/doc/miscellaneous_transformations.html?highlight=threshold#threshold)  compares each pixel to a threshold value and replaces the pixel with a value determined by the threshold type.

* **type** Default value is `THRESH_BINARY`.
* **thresh** Threshold value
* **maxval** For THRESH_BINARY and THRESH_BINARY_INV, the replacement value for the type.

_FireSight_ only:
* **gray** Default value is `true`, which converts input image to grayscale before threshold

#### Model
<pre>{}</pre>

#### Example 1: threshold Pointilism [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1-color.png -Dthresh=1 -Dgray=false</pre>
> Pixel:2ms

The input image appears bland and simple &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

However, setting a threshold of 1 reveals subtle detail &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold1-color.png?raw=true">

#### Example 2: threshold 64 color [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64-color.png -Dthresh=64 -Dgray=false</pre>
> Pixel:2ms

Increasing the threshold to 64 reduces the detail, but accentuates colors &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64-color.png?raw=true">

#### Example 3: threshold 64 grayscale [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64.png -Dthresh=64</pre>
> Pixel:2ms

Converting to grayscale gives the expected mask &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64.png?raw=true">

#### Example 4: threshold type THRESH_BINARY_INV [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64-inv.png -Dthresh=64 -Dtype=THRESH_BINARY_INV</pre>
> Pixel:2ms

Changing the threshold type to THRESH_BINARY_INV produces the following &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64-inv.png?raw=true">
