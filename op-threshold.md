The _FireSight_ wrapper for [OpenCV threshold](http://docs.opencv.org/modules/imgproc/doc/miscellaneous_transformations.html?highlight=threshold#threshold)  compares each pixel to a threshold value and replaces the pixel with a value determined by the threshold type.

* **type** Default value is `THRESH_BINARY`.
* **thresh** Threshold value, normally between 0 and 255. Default is `OTSU`, which will add the THRESH_OTSU flag to **type** for automatic thresholding using [Otsu's method](http://en.wikipedia.org/wiki/Otsu's_method). See Example 5.
* **maxval** For THRESH_BINARY and THRESH_BINARY_INV, the replacement value for the type. Default is `255`, which is ideal for creating image masks for 8-bit images.
* **gray** Default is `true`, which converts image to grayscale. If `false`, each channel will be thresholded, unless Otsu's method is chosen, in which the image is autoatically converted to grayscale. (FireSight only)

_FireSight_ only:
* **gray** Default value is `true`, which converts input image to grayscale before threshold

#### Stage Model
<pre>{}</pre>

#### Example 1: threshold Pointilism [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold1-color.png -Dthresh=1 -Dgray=false</pre>
> [[Pixel]]:0.5ms

The input image appears bland and simple &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

However, setting a threshold of 1 reveals subtle detail &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold1-color.png?raw=true">

#### Example 2: threshold 64 color [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64-color.png -Dthresh=64 -Dgray=false</pre>
> [[Pixel]]:0.5ms

Increasing the threshold to 64 reduces the detail, but accentuates colors &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64-color.png?raw=true">

#### Example 3: threshold 64 grayscale [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64.png -Dthresh=64</pre>
> [[Pixel]]:0.2ms

Converting to grayscale gives the expected mask &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64.png?raw=true">

#### Example 4: threshold type THRESH_BINARY_INV [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/absdiff.png -p json/threshold.json -o target/threshold64-inv.png -Dthresh=64 -Dtype=THRESH_BINARY_INV</pre>
> [[Pixel]]:0.2ms

Changing the threshold type to THRESH_BINARY_INV produces the following &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold64-inv.png?raw=true">

#### Example 5: Otsu's Method [pipeline](https://github.com/firepick1/FireSight/blob/master/json/threshold.json)
<pre>firesight -i img/part1-0.png -p json/threshold.json -o target/threshold-otsu.png -Dthresh=OTSU</pre>
> [[Pixel]]:0.7ms

Otsu's method provides automatic thresholding. As with the preceding examples, the original image is generated via **absdiff** and has many non-zero background pixel differences:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/part1-0.png?raw=true">

Using Otsu's method, we can easily calculate a foreground/background threshold. 
Otsu's method does take more time (compare Example 4), but may be worth the convenience.
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold-otsu.png?raw=true">

### See Also
* [[op absdiff]]
* [[op normalize]]
* [[op minAreaRect]]
