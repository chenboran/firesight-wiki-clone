[OpenCV matchTemplate](http://docs.opencv.org/modules/imgproc/doc/object_detection.html#matchtemplate) wrapper with FireSight extensions. 

Correlation-based template matching is quite powerful. The frequency spectrum of a template is multiplied by the frequency spectrum of an image to obtain the correlation. Maxima (or minima, depending on the method) indicate the candidates for matching. If the images to be recognized are all in a flat plane orthogonal to the camera, there is little or no need to account for perspective skew or near/far size adjustments. For this reason, matchTemplate alone can be used quite effectively in a great majority pick-and-place use cases.

#### Model
<pre>
{
    "maxVal":0.97696870565414429,
    "rects":[
      {
        "x":467.0,
        "y":68.0,
        "width":29.0,
        "height":37.0,
        "angle":0.0,
        "corr":1.0
      },
      {
        "x":518.0,
        "y":69.0,
        "width":29.0,
        "height":37.0,
        "angle":0.0,
        "corr":0.99414855241775513
      },
      {
        "x":711.0,
        "y":71.0,
        "width":29.0,
        "height":37.0,
        "angle":0.0,
        "corr":0.99687016010284424
      },
      {
        "x":760.0,
        "y":71.0,
        "width":29.0,
        "height":37.0,
        "angle":0.0,
        "corr":0.99490123987197876
      }
    ]
  }
</pre>
* **maxVal** The maximum value in the correlation matrix
* **rects** The RotatedRect values of the matched positions
* **x** Center x
* **y** Center y
* **height** Height of rectangle 
* **width** Widht of rectangle
* **corr** Normalized correlation over the interval [0,1], with respect to **maxVal**

#### Example: Find 37x29 rectangles in a pcb image [pipeline]()