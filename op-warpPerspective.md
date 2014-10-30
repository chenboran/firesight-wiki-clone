Applies a perspective transformation to an image.

Reference: [Geometric Image Transformations: warpPerspective()](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#warpperspective)

#### Example
<pre>{"op":"warpPerspective","borderMode":"BORDER_CONSTANT","borderValue":[0,0,0]}</pre>

* **borderMode** pixel extrapolation method (`BORDER_CONSTANT` or `BORDER_REPLICATE`).
* **borderValue** value used in case of a constant border; by default, it equals [0,0,0].

NOTE: Currently, this stage is written with the `flags` parameter hard-coded to `INTER_LINEAR`.

#### Stage Model
<pre>{}</pre>