_FireSight_ wrapper for [OpenCV absdiff](http://opencv.jp/opencv-2svn_org/cpp/core_operations_on_arrays.html#cv-absdiff), which takes the per-channel absolute different of two images. _FireSight_ stage compares specified image with current pipeline image and changes output to the absolute difference.

* **path** Path to second image

#### Model
<pre>{}</pre>

#### Example: Absolute difference green is red [pipeline](https://github.com/firepick1/FireSight/blob/master/json/absdiff.json)
<pre>firesight -i img/pcb.jpg -p json/absdiff.json -Dimg=img/mog2.jpg -o target/absdiff.png</pre>

The pipeline image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

The comparison image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true">

Given that the comparison image is green "FireSight", it may come as a surprise that the absolute difference is partly red. &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

