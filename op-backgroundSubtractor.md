The _FirePick backgroundSubtractor_ stage wraps the [OpenCV BackgroundSubtractor](http://docs.opencv.org/java/org/opencv/video/BackgroundSubtractor.html) class. Background subtraction is excellent for detecting the orientation and offset of objects newly placed on a known background. For pick-and-place operations, this stage can help determine angular and offset error of a picked part. The stage output image is the binary foreground mask computed by the background subtractor.

* **method** The default `absdiff` works well for static images. Method [MOG2](http://docs.opencv.org/modules/video/doc/motion_analysis_and_object_tracking.html#backgroundsubtractormog2) may be more useful for video. 
* **varThreshold** [OpenCV recommends](http://docs.opencv.org/modules/video/doc/motion_analysis_and_object_tracking.html#backgroundsubtractormog2) the default of `16`. Higher values reduce sensitivity and therefore noise.
* **bShadowDetection** (MOG2) The OpenCV and FireSight default is `true`, but _false_ may be more useful given the lack of shadows in most pick-and-place images.
* **background**  (MOG2) If provided, this specifies the path to a fixed background image to compare. 
* **history**  (MOG2) If non-zero, specifies the number of preceding images to aggregate as the background for comparison. The default is `0`. A non-zero value really only matters for video pipelines that need to compute an ever-changing background from the most recent video frames. 
* **learningRate**  (MOG2) Default is `-1`. 

#### Model
<pre>{}</pre>

#### Example 1: BackgroundSubtractorMOG2 varThreshold=16 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/bgsub.json)
<pre>firesight -i img/mog2.jpg -p json/bgsub.json -o target/bgsub.png -DbgImg=img/pcb.jpg -Dmethod=MOG2</pre>
> Pixel:11.8ms Win7/ThinkPad-T410:22.0ms

Background image &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

Background with text &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/mog2.jpg?raw=true"> 

Foreground mask (Windows) &rarr;<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/bgsub-mog2-64.png?raw=true">

Raspberry Pi uses OpenCV 32-bit, and the results are not as good &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/bgsub-mog2.png?raw=true"> 

#### Example 2: BackgroundSubtractorMOG2 varThreshold=64 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/bgsub.json)
<pre>firesight -i img/mog2.jpg -p json/bgsub.json -o target/bgsub-mog2.png -DbgImg=img/pcb.jpg -Dmethod=MOG2 -Dthresh=64 </pre>
> Pixel:11.9ms Win7/ThinkPad-T410:22.0ms

The previous example demonstrates that the 32-bit OpenCV version of BackgroundSubtractorMOG2 does not work as well as the 64-bit version of OpenCV. However, we can improve our results by using the _varThreshold_, which is bound to the `thresh` pipeline parameter. To reduce noise artifacts, we increase _varThreshold_ from the default `16` to `64`:

_varThreshold_ set to `64` &rarr;
<img src="https://github.com/firepick1/FireSight/blob/master/img/bgsub-mog2-64.png?raw=true"> 

#### Example 3: absdiff method, thresh=32 [pipeline](https://github.com/firepick1/FireSight/blob/master/json/bgsub.json)
<pre>firesight -i img/mog2.jpg -p json/bgsub.json -o target/bgsub-absdiff.png -DbgImg=img/pcb.jpg -Dmethod=absdiff -Dthresh=32 -Dmethod=absdiff</pre>
> Pixel:2.4ms Win7/ThinkPad-T410:9.7ms RaspberryPi:

Thanks to Chris, who pointed out that a faster and simpler method of background subtraction 
can be had by simply combining [absdiff](op absdiff) and [threshold](op threshold). As you can see, setting _method_ to _absdiff_ is 6x faster and results in cleaner output:

<img src="https://github.com/firepick1/FireSight/blob/master/img/bgsub-absdiff.png?raw=true"> 

#### See Also
* [[op erode]]
* [[op dilate]]
* [[op absdiff]]
* [[op threshold]]
