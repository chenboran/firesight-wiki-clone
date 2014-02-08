Discrete Fourier Transform [OpenCV dft](http://docs.opencv.org/modules/core/doc/operations_on_arrays.html#dft) wrapper. 

The _dft_ stage changes the data format of the pipeline working Mat. It creates a CV_32F complex Mat on forward transform. It creates a CV_8U Mat on inverse transform. The dynamic range of the complex spectrum is too large to be visually meaningful. To visualize the spectrum, see [[op: dftSpectrum]].

* **flags** JSON array of strings representing bits to be OR'd: `DFT_SCALE`, `DFT_INVERSE`, `DFT_COMPLEX_OUTPUT`, `DFT_REAL_OUTPUT`. 

#### Model
<pre>{}</pre>

#### Examples

##### DFT of white rectangle [pipeline](https://github.com/firepick1/FireSight/blob/master/json/dft-rect2.json)
<pre>firesight -p json/dft-rect2.json -o target/dft-rect.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true">

<img src="https://github.com/firepick1/FireSight/blob/master/img/dft-rect.jpg?raw=true">

#### See Also
[[op: dftSpectrum]]

