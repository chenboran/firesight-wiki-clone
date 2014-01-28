[MSER](http://docs.opencv.org/modules/features2d/doc/feature_detection_and_description.html#mser) wrapper

#### Pipeline
<pre>{"op":"MSER", "color":[255, 0, 255], "minArea":1100, "maxArea":1200}</pre>

* **delta** delta, in the code, it compares (size_{i}-size_{i-delta})/size_{i-delta}. default `5.
* **minArea** prune the area which smaller than minArea. default `60`
* **maxArea** prune the area which bigger than maxArea. default `14400`
* **maxVariation** prune the area have simliar size to its children. default `0.25`
* **minDiversity** trace back to cut off mser with diversity < min_diversity. default `0.2`
* **maxEvolution** for color image, the evolution steps. default `200`
* **areaThreshold** the area threshold to cause re-initialize. default `1.01`
* **minMargin** ignore too small margin. default `0.003`
* **edgeBlurSize** the aperture size for edge blur. default `5`

#### Model
<pre>{}</pre>

#### Examples
<pre>firesight -i img/MSER_phj -p img/MSER_phj.json</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phj.jpg?raw=true">