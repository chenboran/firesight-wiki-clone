[SimpleBlobDetector](http://docs.opencv.org/modules/features2d/doc/common_interfaces_of_feature_detectors.html#simpleblobdetector)  wrapper

#### Pipeline
<pre>{"op":"SimpleBlobDetector", "thresholdStep":10}</pre>
Stage attribute values (e.g., "thresholdStep") correspond to the fields of [SimpleBlobDetector::Params](http://docs.opencv.org/modules/features2d/doc/common_interfaces_of_feature_detectors.html#simpleblobdetector)

#### Stage Model
<pre>{"keypoints":[{"x":1,"y":2,"size":15.6,"angle":20.2,"response":1}]}</pre>
* **angle** is omitted if -1
* **response** is omitted if 0

#### Example
<pre>firepick -i img/cam.jpg -p json/SimpleBlobDetector.json</pre>
Grayscale working image is written to `target/SimpleBlobDetector.jpg`

#### See Also
* [[op drawKeypoints]]
* [[op HoleRecognizer]]
