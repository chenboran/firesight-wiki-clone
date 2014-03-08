FireSight op draws _RotatedRect_ array from named stage model.  Because some folks like square corners, while others are well-rounded.

#### Pipeline
<pre>{"op":"drawRects","model":"s2", "color":[255, 0, 255], "flags":5}</pre>
* **model** name of stage that generates _rects_ model to be drawn
* **color** JSON array corresponding to cv::Scalar with 1-4 elements (`[-1 -1 -1 -1]` default)

#### Model
<pre>{}</pre>

#### Example [pipeline](https://github.com/firepick1/FireSight/blob/master/json/drawRects.json)
<pre>firesight -i img/ass_place_phj.jpg -p json/drawRects.json -o target/drawRects.jpg</pre>
Output image saved as `target/drawRects.jpg`

<img src="https://github.com/firepick1/FireSight/blob/master/img/drawRects.jpg?raw=true">

#### See Also
* [[op SimpleBlobDetector]]
* [[op drawKeypoints]]
