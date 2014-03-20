_FireSight_ wrapper for [OpenCV threshold](http://docs.opencv.org/modules/imgproc/doc/miscellaneous_transformations.html?highlight=threshold#threshold), which compares each pixel to a threshold value and replaces the pixel with a value determined by the threshold type.

* **type** Default value is `THRESH_BINARY`.
* **thresh** Threshold value
* **maxval** For THRESH_BINARY and THRESH_BINARY_INV, the replacement value for the type.

#### Model
<pre>{}</pre>

#### Example: threshold Pointilism [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1.png -Dthresh=1</pre>
> Pixel:0.3ms

The input image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

The threshold image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold1.png?raw=true">
