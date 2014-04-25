[OpenCV drawKeypoints](http://docs.opencv.org/modules/features2d/doc/drawing_function_of_keypoints_and_matches.html#drawkeypoints) wrapper

#### Pipeline
<pre>{"op":"drawKeypoints","model":"s2", "color":[255, 0, 255], "flags":5}</pre>
* **model** name of stage that generates _keypoints_ model to be drawn
* **color** JSON array corresponding to cv::Scalar with 1-4 elements (`[-1 -1 -1 -1]` default)
* **flags** int value of desired DrawMatchesFlags (5 is more informative than the default value of `0`)

#### Stage Model
<pre>{}</pre>

#### Example
<pre>firesight -i img/cam.jpg -p json/drawKeypoints.json</pre>
Output image saved as `target/drawKeypoints.jpg`
<img src="https://github.com/firepick1/FireSight/blob/master/img/drawKeypoints.jpg?raw=true">

#### See Also
* [[op SimpleBlobDetector]]
* [[op drawRects]]
