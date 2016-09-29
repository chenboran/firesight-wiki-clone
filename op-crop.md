Crops current pipeline image to given (x,y,width,height) rectangle

#### Pipeline
<pre>{"op":"crop","x":0,"y":0,"width":64,"height":64}</pre>

#### Stage Model
<pre>{}</pre>

#### Example 1: Duck eyes [pipeline](https://github.com/firepick1/FireSight/blob/master/json/crop.json)
<pre>firesight -i img/duck.jpg -p json/crop.json -o crop.png -Dx=50 -Dy=75 -Dwidth=100 -Dheight=50</pre>
> Pixel: 3ms

duck.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.jpg?raw=true">

crop.png &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/crop.png?raw=true">

#### See Also
