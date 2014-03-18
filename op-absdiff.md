_FireSight_ wrapper for [OpenCV absdiff](http://opencv.jp/opencv-2svn_org/cpp/core_operations_on_arrays.html#cv-absdiff), which takes the per-channel absolute difference of two images. _FireSight_ stage compares specified image with current pipeline image and changes output to the absolute difference of the two.

* **path** Path to second image

#### Model
<pre>{}</pre>

#### Example: Green is red [pipeline](https://github.com/firepick1/FireSight/blob/master/json/absdiff.json)
<pre>firesight -i img/pcb.jpg -p json/absdiff.json -Dimg=img/mog2.jpg -o target/absdiff.png</pre>
> Pixel:4ms

The pipeline image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

The comparison image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true">

Note that the absolute difference of the two is red and green. This happens because the absolute difference is a per-channel difference of each color. <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/absdiff.png?raw=true">

