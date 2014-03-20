_FireSight_ wrapper for [OpenCV threshold](http://docs.opencv.org/modules/imgproc/doc/miscellaneous_transformations.html?highlight=threshold#threshold), which compares each pixel to a threshold value and replaces the pixel with a value determined by the threshold type.

* **type** Default value is `THRESH_BINARY`.
* **thresh** Threshold value
* **maxval** For THRESH_BINARY and THRESH_BINARY_INV, the replacement value for the type.

#### Model
<pre>{}</pre>

#### Example: threshold Pointilism [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1.png -Dthresh=1</pre>
> Pixel:0.3ms

The input image appears bland and simple &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

Setting a threshold of 1 reveals the subtle detail in the image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold1.png?raw=true">

#### Example: threshold 64 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1.png -Dthresh=64</pre>
> Pixel:0.3ms

Increasing the threshold to 65 reduces the detail &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64.png?raw=true">

#### Example: grayscale threshold 64 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1.png -Dthresh=64 -Dcvt=cvtColor</pre>
> Pixel:0.5ms

Converting to grayscale gives the expected mask &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshol.png?raw=true">
