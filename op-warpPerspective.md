Applies a perspective transformation to an image.

Reference: [Geometric Image Transformations: warpPerspective()](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#warpperspective)

#### Example
<pre>{"op":"warpPerspective","borderMode":"BORDER_CONSTANT","borderValue":[0,0,0]}</pre>

* **borderMode** pixel extrapolation method (`BORDER_CONSTANT` or `BORDER_REPLICATE`).
* **borderValue** value used in case of a constant border; by default, it equals [0,0,0].

NOTE: Currently, this stage is written with the `flags` parameter hard-coded to `INTER_LINEAR`.

#### Stage Model
<pre>{}</pre>

#### Example: A different perspective [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid-perspective.json)
<pre>firesight -i img/cal-grid.png -p json/matchGrid-perspective.json -Dtemplate=img/cross32.png</pre>
In this example, we used [[op-matchGrid]] to give us a perspective matrix that makes 
a dramatic difference.

<pre>
"perspective":[
1.0405136564383939,    0.026744906574870872, -2.943810346145538,
0.024529984309304427,  1.097007339310166,    -14.050588819421538,
-1.7780681696463529e-5,0.00027266213560320576,1.0
],
</pre>

**Distorted image**<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/cal-grid.png?raw=true">

**Undistorted image**<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchGrid-perspective.png?raw=true">
