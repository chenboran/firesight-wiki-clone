Discrete Fourier Transform [OpenCV dft](http://docs.opencv.org/modules/core/doc/operations_on_arrays.html#dft) wrapper with some FireSight goodies.

* **flags** JSON array of strings representing bits to be OR'd: `DFT_SCALE`, `DFT_INVERSE`, `DFT_COMPLEX_OUTPUT`, `DFT_REAL_OUTPUT`. Creates a CV_32F 2D Mat on forward transform. Creates a CV_8U Mat on inverse transform.

#### Model
<pre>{}</pre>

#### Examples

##### DFT of white rectangle [pipeline](https://github.com/firepick1/FireSight/blob/master/json/dft-rect2.json)
<pre>firesight -p json/dft-rect2.json -o target/dft-rect.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true">

<img src="https://github.com/firepick1/FireSight/blob/master/img/dft-rect.jpg?raw=true">

#### See Also
[[op: dftSpectrum]]

