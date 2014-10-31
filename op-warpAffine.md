FireSight wrapper for OpenCV [warpAffine](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#warpaffine):

* **angle** Rotate image counter-clockwise by given angle in degrees. Default `0`
* **cx** Center of rotation. Default is center of image
* **cy** Center of rotation. Default is center of image
* **dx** Translation after rotation. Default is `0`
* **dy** Translation after rotation. Default is `0`
* **width** Width of output image. Default is width of original image. _FireSight:_ If `-1`, width will be automatically computed to show full image (vs. cropping it).
* **height** Height of output image. Default is height of original image. _FireSight:_ If `-1`, height will be automatically computed to show full image (vs. cropping it).
* **scale** Size scale of output image. Default is `1`
* **reflect** JSON vector of [x,y] reflection vector. Default is `[0,0]`. Only x-, y- and xy-axis reflections are supported because of a bug in OpenCV.
* **borderValue** Color to use for background. Default is `[0,0,0]` BGR
* **borderMode** Specifies how border of transformed image should be filled: `BORDER_CONSTANT` fills with _borderValue_; `BORDER_REPLICATE` replicates border pixels; `BORDER_REFLECT` fills with a mirror image of source image doubling the border value; `BORDER_REFLECT_101` fills with a mirror image of source image without doubling the border value; `BORDER_WRAP` fills with repeated copies of the source image.

#### Stage Model
<pre>{}</pre>

#### Example: Rotate a duck by 30 degrees and scale it by 0.5 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/warpAffine-rotate.json)
<pre>firesight -i img/duck.jpg -p json/warpAffine-rotate.json -o target/warpAffine-rotate.jpg</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.jpg?raw=true">&nbsp;<img src="https://github.com/firepick1/FireSight/blob/master/img/warpAffine-rotate.jpg?raw=true">

#### Example: Rotate a duck by 30 degrees with BORDER_REPLICATE [pipeline](https://github.com/firepick1/FireSight/blob/master/json/warpAffine-rotate2.json)
<pre>firesight -i img/duck.jpg -p json/warpAffine-rotate2.json -o target/warpAffine-rotate2.jpg</pre>
The choice of border fill when rotating an image can strongly influence the use of that image as a template for matching. Using BORDER_REPLICATE can greatly improve matching accuracy:

<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.jpg?raw=true">&nbsp;<img src="https://github.com/firepick1/FireSight/blob/master/img/warpAffine-rotate2.jpg?raw=true">

#### Example: Translate a duck by (50,50) pixels [pipeline](https://github.com/firepick1/FireSight/blob/master/json/warpAffine-translate.json)
<pre>firesight -i img/duck.jpg -p json/warpAffine-translate.json -o target/warpAffine-translate.jpg</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.jpg?raw=true">&nbsp;<img src="https://github.com/firepick1/FireSight/blob/master/img/warpAffine-translate.jpg?raw=true">

#### Example: Flip a duck [pipeline](https://github.com/firepick1/FireSight/blob/master/json/fliph.json)
<pre>firesight -i img/duck.png -p json/fliph.json -o target/fliph.png</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.png?raw=true">&nbsp;<img src="https://github.com/firepick1/FireSight/blob/master/img/warpAffine-h.png?raw=true">
