The _putText_ operation provides the function of [OpenCV putText](http://docs.opencv.org/modules/core/doc/drawing_functions.html#puttext), and allows you to put text into your pipeline image.

* **text** The text to put into image
* **org** The bottom-left corner of the text. If org.y is negative, it is relative to the image bottom. Default is `[5,-6]`
* **fontFace** Font type. One of FONT_HERSHEY_SIMPLEX, FONT_HERSHEY_PLAIN, FONT_HERSHEY_DUPLEX, FONT_HERSHEY_COMPLEX, FONT_HERSHEY_TRIPLEX, FONT_HERSHEY_COMPLEX_SMALL, FONT_HERSHEY_SCRIPT_SIMPLEX, or FONT_HERSHEY_SCRIPT_COMPLEX. Default is `FONT_HERSHEY_PLAIN`
* **italic** Default is `false`
* **color** BGR JSON array of [0..255]. Default is `[0,255,0]`
* **thickness** Default is `1`
* **fontScale** Default is `1.0`

#### Model 
<pre>{}</pre>

#### Example 1: Quack [