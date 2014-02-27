_FireSight_ wrapper for [OpenCV resize()](http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#resize)

* **fx** Horizontal scale, default `1`
* **fy** Vertical scale, default `1`

#### Model
<pre>{}</pre>

#### Example: Squeeze the Duck [pipeline](https://github.com/firepick1/FireSight/blob/master/json/resize.json)
<pre>firesight -i img/duck.jpg -p json/resize.json -o target/resize.jpg -Dfx=0.25 -Dfy=0.5</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.jpg?raw=true"> &larr;Original Duck
<img src="https://github.com/firepick1/FireSight/blob/master/img/resize.jpg?raw=true"> &larr;Squeezed Duck
