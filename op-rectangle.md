The _rectangle_ operation provides the function of 
[OpenCV rectangle](http://docs.opencv.org/modules/core/doc/drawing_functions.html#rectangle), 
and allows you to put a rectangle into your pipeline image.

* **x** The x-coordinate of the left edge of the rectangle. _FireSight:_ If -1, center the rectangle horizontally
* **y** The y-coordinate of the top edge of the rectangle. _FireSight:_ If -1, center the rectangle vertically
* **width** The width of the rectangle. _FireSight:_ Default is 64.
* **height** The width of the rectangle. _FireSight:_ Default is 64.
* **fill** _FireSight:_ JSON array of BGR color to fill rectangle. Default is [-1,-1,-1] for no fill.
* **thickness** border thickness. Default is 1.
* **color** border color. Default is [0,0,0].
* **lineType** [Default is 8](http://docs.opencv.org/modules/core/doc/drawing_functions.html#linea)
* **flood** _FireSight: Color for outside of rectangle. Default is [-1,-1,-1] for no flood.
* **shift** Number of fractional bits in the point coordinates. Default is 0.

#### Stage Model 
<pre>{}</pre>

#### Example 1: Parma Flag [pipeline](https://github.com/firepick1/FireSight/blob/master/json/crosshair.json)
<pre>firesight -p json/crosshair.json -o target/crosshair.png -Dbackground=[0,255,255] -Dcolor=[255,0,0] -Dsize=8</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/crosshair.png?raw=true">
