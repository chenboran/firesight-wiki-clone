[OpenCV MSER](http://docs.opencv.org/modules/features2d/doc/feature_detection_and_description.html#mser) wrapper with FireSight filtering extensions.

#### Pipeline
<pre>{"op":"MSER", "color":[255, 0, 255], "minArea":1100, "maxArea":1200}</pre>

* **delta** delta, in the code, it compares (size_{i}-size_{i-delta})/size_{i-delta}. Larger delta yields fewer images. Default `5`
* **minArea** prune the blobs whose area is smaller than minArea. Default `60`
* **maxArea** prune the blobs whose area is bigger than maxArea. Default `14400`
* **maxVariation** prune the area have simliar size to its children. Default `0.25`
* **minDiversity** trace back to cut off mser with diversity < min_diversity. Default `0.2`
* **maxEvolution** for color image, the evolution steps. Default `200`
* **areaThreshold** the area threshold to cause re-initialize. Default `1.01`
* **minMargin** ignore too small margin. Default `0.003`
* **edgeBlurSize** the aperture size for edge blur. Default `5`
* **mask** If provided, a JSON object (x,y,width,height) specifies MSER mask rectangle. By default, entire image is processed. 

The following pipeline parameters are exclusive to _FireSight_: 
* **color** if provided, matched regions will be colored with BGR Scalar having 1-4 values. For alternating colors, use: [-1,-1,-1,-1]
* **detect** `keypoints` adds a KeyPoint JSON object to the stage model for each detected MSER region. Each KeyPoint is determined from eigenvectors and covariance matrix of region. The _size_ field of the KeyPoint is calculated from the number of points in the region: _size = 2*sqrt(region.size()/&pi;)_
* **detect** `rects` adds a RotatedRect JSON object to the stage model for each detected MSER region. Each RotatedRect is calculated by _minAreaRect()_ 

#### Stage Model
If `"detect":"keypoints"` is specified, a stage model KeyPoint is added for each MSER region detected. The following model corresponds with the _MSER with keypoints_ example below:
<pre>
 "mser":{
    "keypoints":[
      {
        "pt.x":209.50672912597656,
        "pt.y":71.5,
        "size":38.892269134521484,
        "angle":359.97735595703125
      },
      {
        "pt.x":121.55968475341797,
        "pt.y":72.026527404785156,
        "size":37.947780609130859,
        "angle":359.83328247070312
      }
    ]
  }
</pre>

If `"detect":"rects"` is specified, the stage model is updated with a JSON object for each region's _minAreaRect()_ RotatedRect:
<pre>
{
    "rects":[
      {
        "x":209.0,
        "y":71.0,
        "width":54.0,
        "height":22.0,
        "angle":0.0
      },
      {
        "x":121.5,
        "y":72.0,
        "width":53.0,
        "height":20.0,
        "angle":-0.0
      }
    ]
  }
</pre>
#### Examples
In the following examples, output image is written to `target/MSER.jpg`

##### MSER with `"detect":"keypoints"` [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phj.json)
<pre>firesight -i img/ass_place_phj.jpg -p json/MSER_phj.json -o target/MSER.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phj.jpg?raw=true">

##### MSER with Mask [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phf.json)
<pre>firesight -i img/ass_place_phf.jpg -p json/MSER_phf.json -o target/MSER.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phf.jpg?raw=true">

##### Grayscale MSER with Mask [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phh.json)
<pre>firesight -i img/ass_place_phh.jpg -p json/MSER_phh.json -o target/MSER.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phh.jpg?raw=true">

##### MSER with `"detect":"keypoints"` and `"detect":"rects"` [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phj2.json)
<pre>firesight -i img/ass_place_phj.jpg -p json/MSER_phj2.json -o target/MSER_phj2.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phj2.jpg?raw=true">
