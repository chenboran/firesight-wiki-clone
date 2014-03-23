The _FireSight_ command line application is `firesight`. Options are:

* **-Dname=value** define value for a [pipeline parameter](Pipeline Parameters)
* **-debug** if present, print out debug level logging information. Default level is (trace,debug,**info**,warn,error).
* **-i** _image-file-path_ Optional input image. See also [[op: imread]]
* **-ji** _JSON-indent_ Option value for JSON indent. Default is `2`. A value of `0` will not insert line breaks or indents. 
* **-o** _output-image-path_ Optional output image path. See also [[op: imwrite]]
* **-p** _JSON-pipeline-file-path_
* **-trace** if present, print out trace level logging information. Default level is (trace,debug,**info**,warn,error)
* **-video** VideoCapture() to window. See [sample video by Paul Jones](https://www.youtube.com/watch?v=Hzi3dY2WU0k) 

#### See Also
* [[lib_firesight.so]]
* [[Pipeline Parameters]]
* [[Build FireSight (Linux)]]
* [[Build FireSight (Windows)]]