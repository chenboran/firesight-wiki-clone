[MSER](http://docs.opencv.org/modules/features2d/doc/feature_detection_and_description.html#mser) wrapper

#### Pipeline
<pre>{"op":"MSER", "color":[255, 0, 255], "minArea":1100, "maxArea":1200}</pre>

* **delta** delta, in the code, it compares (size_{i}-size_{i-delta})/size_{i-delta}. Larger delta yields fewer images. Default `5`
* **minArea** prune the area which smaller than minArea. Default `60`
* **maxArea** prune the area which bigger than maxArea. Default `14400`
* **maxVariation** prune the area have simliar size to its children. Default `0.25`
* **minDiversity** trace back to cut off mser with diversity < min_diversity. Default `0.2`
* **maxEvolution** for color image, the evolution steps. Default `200`
* **areaThreshold** the area threshold to cause re-initialize. Default `1.01`
* **minMargin** ignore too small margin. Default `0.003`
* **edgeBlurSize** the aperture size for edge blur. Default `5`
* **mask** If provided, a JSON object (x,y,width,height) specifies MSER mask rectangle. By default, entire image is processed. 
* _FireSight_:**color** if provided, matched regions will be colored with BGR Scalar having 1-4 values. For alternating colors, use: [-1,-1,-1,-1]

#### Model
<pre>{}</pre>
TBD: The MSER regions are a bit verbose for the model, but perhaps a KeyPoint summary might be useful.

#### Examples
In the following examples, output image is written to `target/MSER.jpg`

##### Simple MSER [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phj.json)
<pre>firesight -i img/MSER_phj -p json/MSER_phj.json</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phj.jpg?raw=true">

##### MSER with Mask [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phf.json)
<pre>firesight -i img/MSER_phf -p json/MSER_phf.json</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phf.jpg?raw=true">

##### Grayscale MSER with Mask [pipeline](https://github.com/firepick1/FireSight/blob/master/json/MSER_phh.json)
<pre>firesight -i img/MSER_phh -p json/MSER_phh.json</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/MSER_phh.jpg?raw=true">