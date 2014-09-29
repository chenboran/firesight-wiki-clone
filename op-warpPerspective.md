FireSight wrapper for OpenCV [warpPerspective](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#warpperspective):

* **matrix** Transformation matrix to apply on the image. Default is identity matrix.
* **borderValue** Color to use for background. Default is `[0,0,0]` BGR
* **borderMode** Specifies how border of transformed image should be filled: `BORDER_CONSTANT` fills with _borderValue_; `BORDER_REPLICATE` replicates border pixels; `BORDER_REFLECT` fills with a mirror image of source image doubling the border value; `BORDER_REFLECT_101` fills with a mirror image of source image without doubling the border value; `BORDER_WRAP` fills with repeated copies of the source image.

#### Stage Model
<pre>{}</pre>

#### Example: Rotate a duck by 30 degrees and scale it by 0.5
<pre>"matrix":[0.433, 0.25, 0, -0.25, 0.433, 0, 0, 0, 1]</pre>

![Duck](https://github.com/simonfojtu/FireSight/raw/master/img/duck.jpg)&nbsp;![Duck -30deg, 0.5scale](https://github.com/simonfojtu/FireSight/raw/master/img/duck_-30deg_0.5scale.jpg)

#### Example: Invert x and y axes.
<pre>"matrix":[0, 1, 0, 1, 0, 0, 0, 0, 1]</pre>

![Duck](https://github.com/simonfojtu/FireSight/raw/master/img/duck.jpg)&nbsp;![Duck -30deg, 0.5scale](https://github.com/simonfojtu/FireSight/raw/master/img/duck_xy_inv.jpg)
