Compute minimum area RotatedRect for a range of pixel intensity values in a selected image channel. 
This _FireSight_ operation relies on 
[OpenCV minAreaRect](http://docs.opencv.org/modules/imgproc/doc/structural_analysis_and_shape_descriptors.html?highlight=minarearect#minarearect).

* **min** Default value is `1`. Minimum pixel value to consider.
* **max** Default value is `255`. Maximum pixel value to consider.
* **channel** Default value is `0`. Index of BGR image channel.

#### Stage Model
The **minAreaRect** operation is actually a fast single blob detector, and provides a single RotatedRect in the model using the 
JSON structure expected by [[op drawRects]]. The number of points in the RotatedRect region is also given so you can compute region density.
<pre>
{
  "rects":[
    {
      "x":62.514705657958984,
      "y":127.30883026123047,
      "width":43.560646057128906,
      "height":27.268278121948242,
      "angle":-59.036239624023438
    }
  ],
  "points":792
}
</pre>

#### Example 1: Find bright green things [pipeline](https://github.com/firepick1/FireSight/blob/master/json/minAreaRect.json)
<pre>firesight -i img/abc-color.png -p json/minAreaRect.json -o target/minAreaRect.png -Dmin=128 -Dchannel=1 -Dthickness=1</pre>
> [[Pixel]]:0.4ms [[RPi]]:11ms

Consider a colorful picture:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/abc-color.png?raw=true">

We can find and box all bright green things using **channel=1** and **min=128**:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/minAreaRect-abc.png?raw=true"> 

#### Example 2: Detect a part [pipeline](https://github.com/firepick1/FireSight/blob/master/json/minAreaRect-thresh.json)
<pre>firesight -i img/part1-0.png -p json/minAreaRect-thresh.json -o target/minAreaRect-thresh.png</pre>
> [[Pixel]]:3.6ms [[RPi]]:150ms

Suppose we have a pick-and-place head with no part:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/part0.png?raw=true">

We then pick up a part:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/part1.png?raw=true">

Using [[op absdiff]] we get:</br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/part1-0.png?raw=true">

Starting with the absdiff'ed image, the pipeline uses [[op threshold]] to generate this image with Otsu's method:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/threshold-otsu.png?raw=true">

Finally, the **minAreaRect** stage itself gives us:<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/minAreaRect-thresh.png?raw=true">

