
_FireSight_ wrapper for 
[OpenCV mesnStdDev](http://opencv.jp/opencv-2svn_org/cpp/core_operations_on_arrays.html#cv-meanstddev), 
which computes the mean and standard deviation of image pixel intensities.

* **path** Path to second image

#### Stage Model
Mean and standard deviation values are provided as blue, green, red values (BGR):
<pre> {
  "s1":{
    "mean":[
      57.865975609756099,
      118.61485772357723,
      178.11601626016261,
      0.0
    ],
    "stdDev":[
      67.547801238063741,
      55.596208075900137,
      40.276437507259224,
      0.0
    ]
  }
}
</pre>

#### Example: Not all green [pipeline](https://github.com/firepick1/FireSight/blob/master/json/meanStdDev.json)
<pre>firesight -i img/duck.jpg -p json/meanStdDev.json</pre>

