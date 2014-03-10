The _FirePick backgroundSubtractor_ stage wraps the [OpenCV BackgroundSubtractor](http://docs.opencv.org/java/org/opencv/video/BackgroundSubtractor.html) class. Background subtraction is excellent for detecting the orientation and offset of objects newly placed on a known background. For pick-and-place operations, this stage can help determine angular and offset error of a picked part. The stage output image is the binary foreground mask computed by the background subtractor.

* **method** The default `MOG2` is the only [supported method](http://docs.opencv.org/modules/video/doc/motion_analysis_and_object_tracking.html#backgroundsubtractormog2). 
* **bShadowDetection** The OpenCV and FireSight default is `true`, but _false_ may be more useful given the lack of shadows in most pick-and-place images.
* **varThreshold** [OpenCV recommends](http://docs.opencv.org/modules/video/doc/motion_analysis_and_object_tracking.html#backgroundsubtractormog2) the default of `16`. Higher values reduce sensitivity and therefore noise.
* **background** If provided, this specifies the path to a fixed background image to compare. 
* **history** If non-zero, specifies the number of preceding images to aggregate as the background for comparison. The default is `0`. A non-zero value really only matters for video pipelines that need to compute an ever-changing background from the most recent video frames. 
* **learningRate** Default is `-1`. 

#### Model
<pre>{}</pre>

#### Example: Detect text overlay in image [pipeline](https://github.com/firepick1/FireSight/blob/master/json/mog2-fgMask.json)
<pre>firesight -i img/mog2.jpg -p json/mog2-fgMask.json -o target/mog2-fgMask.png -DbgImg=img/pcb.jpg</pre>

Background image &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

Background with text &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true"> 

Foreground mask (Windows) &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2-fgMask-win.png?raw=true">

Since Raspberry Pi is based on older OpenCV 2.3, the results are not as good &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2-fgMask.png?raw=true"> 

#### Example: Detect text overlay in image [pipeline](https://github.com/firepick1/FireSight/blob/master/json/mog2-fgMask.json)
<pre>firesight -i img/mog2.jpg -p json/mog2-fgMask.json -o target/mog2-fgMask64.png -DbgImg=img/pcb.jpg -Dvt=64</pre>
The previous example demonstrates that the Raspberry Pi (or at least OpenCV 2.3) version of BackgroundSubtractorMOG2 does not work as well as the 2.4.8 version of OpenCV. However, we can improve our results by using the _varThreshold_, which is bound to the `vt` pipeline parameter. To reduce noise artifacts, we increase _varThreshold_ from the default `16` to `64`:

_varThreshold_ set to `64` &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2-fgMask64.png?raw=true"> 

#### See Also
* [[op erode]]
* [[op dilate]]