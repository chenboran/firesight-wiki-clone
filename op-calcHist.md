The _FireSight_ **calcHist** stage is primarily diagnostic and provides only a subset of the functionality of [OpenCV calcHist](http://docs.opencv.org/modules/imgproc/doc/histograms.html?highlight=histogram#histograms). 

* **accumulate** If true, bin values for separate channels will be summed. Default is `false`
* **channels** is a JSON vector of channel indexes. The default is `[]`, which will use all image channels. For an RGB image, this will be identical to `[0 1 2]`. For a monochrome image, this will be identical to `[0]`. The maximum number of channels in the array is 4.
* **dims** histogram dimensions. Default is `1`. At this time, only 1 dimension is supported.
* **rangeMax** maximum (exclusive)( value to use for range. Default is `256`
* **rangeMin** minimum (inclusive) value to use for range. Default is `0`

The current _FireSight_ implementation of **calcHist** only supports 1-dimensional histograms. Future implementations may support the full capability of OpenCV.

#### Model
For single channel images or if _accumulate_ is true, the histogram model is a sparse JSON object of integers:
<pre>{
"hist":{
   "0":40751,
   "1":60157,
...
   "216":2
  }
}</pre>

For convenience, _FireSight_ will generate one histogram for each channel of a color image if _accumulate_ is false. The histogram values are combined into JSON arrays for each histogram bin:
<pre>{
"hist":{
   "0":[28983,40751,35947],
   "1":[44643,60157,53446],
...
  "236":[0,0,1]
  }
}</pre>

#### Example 1: multi-channel histogram [pipeline](https://github.com/firepick1/FireSight/blob/master/json/calcHist.json)
<pre>firesight -i img/threshold64-color.png  -p json/calcHist.json -ji 0</pre>
> [[Pixel]]:1.3ms

The input color image is the result of a [threshold](op threshold) pipeline &rarr; <br>
<img src="https://raw.githubusercontent.com/firepick1/FireSight/master/img/threshold64-color.png">

The resulting **calcHist** model demonstrates that the threshold operation concentrated all pixel values for each channel into either 0 or 255:
<pre>{
  "FireSight":{"version":"0.8.5","url":"https://github.com/firepick1/FireSight"},
  "s1":{
    "hist": {"0":[159711,159329,159260],"255":[289,671,740]}
  }
}</pre>