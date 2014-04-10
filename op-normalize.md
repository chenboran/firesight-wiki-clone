_FireSight_ wrapper for [OpenCV normalize](http://docs.opencv.org/modules/core/doc/operations_on_arrays.html#normalize), which scales the dynamic range of the pixels in an image.

* **alpha** Default `1`. Norm value to normalize to or the lower range boundary in case of the range normalization.
* **beta** Default `0`. Upper range boundary in case of the range normalization; it is not used for the norm normalization.
* **normType** normalization type ([NORM_L2](http://mathworld.wolfram.com/L2-Norm.html) (default), [NORM_L1](http://mathworld.wolfram.com/L1-Norm.html), NORM_MINMAX, [NORM_INF](http://mathworld.wolfram.com/L-Infinity-Norm.html)).

#### Model
<pre>{}</pre>

#### Example: Not all green [pipeline](https://github.com/firepick1/FireSight/blob/master/json/absdiff.json)
<pre>firesight -i img/pcb.jpg -p json/absdiff.json -Dimg=img/mog2.jpg -o target/absdiff.png</pre>
> Pixel:4ms

The pipeline image &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">
