The _putText_ operation provides the function of [OpenCV putText](http://docs.opencv.org/modules/core/doc/drawing_functions.html#puttext), and allows you to put text into your pipeline image.

* **text** The text to put into image
* **org** The bottom-left corner of the text. If org.y is negative, it is relative to the image bottom. Default is `[5,-6]`
* **fontFace** Font type. One of FONT_HERSHEY_SIMPLEX, FONT_HERSHEY_PLAIN, FONT_HERSHEY_DUPLEX, FONT_HERSHEY_COMPLEX, FONT_HERSHEY_TRIPLEX, FONT_HERSHEY_COMPLEX_SMALL, FONT_HERSHEY_SCRIPT_SIMPLEX, or FONT_HERSHEY_SCRIPT_COMPLEX. Default is `FONT_HERSHEY_PLAIN`
* **italic** Default is `false`
* **color** JSON array of BGR values between 0 and 255. Default is `[0,255,0]`
* **thickness** Default is `1`
* **fontScale** Default is `1.0`

#### Model 
<pre>{}</pre>

#### Example 1: Quirky Duck [pipeline](https://github.com/firepick1/FireSight/blob/master/json/putText.json)
<pre>firesight -i img/duck.png -p json/putText.json -o target/putText.png -Dtext="Quirky Duck" -Dcolor=[64,0,0]</pre>

Input image &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/duck.png?raw=true">
Image with text &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/putText.png?raw=true">
