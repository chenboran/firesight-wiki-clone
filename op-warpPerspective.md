FireSight wrapper for OpenCV [warpPerspective](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#warpperspective):

* **matrix** Transformation matrix to apply on the image. Default is identity matrix.
* **borderValue** Color to use for background. Default is `[0,0,0]` BGR
* **borderMode** Specifies how border of transformed image should be filled: `BORDER_CONSTANT` fills with _borderValue_; `BORDER_REPLICATE` replicates border pixels; `BORDER_REFLECT` fills with a mirror image of source image doubling the border value; `BORDER_REFLECT_101` fills with a mirror image of source image without doubling the border value; `BORDER_WRAP` fills with repeated copies of the source image.

#### Stage Model
<pre>{}</pre>
