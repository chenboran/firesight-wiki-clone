Discrete Fourier Transform [OpenCV dft](http://docs.opencv.org/modules/core/doc/operations_on_arrays.html#dft) wrapper. 

The _dft_ stage changes the data format of the pipeline working Mat. It creates a CV_32F complex Mat on forward transform. It creates a CV_8U Mat on inverse transform. The dynamic range of the complex spectrum is too large to be visually meaningful. To visualize the spectrum, see [[op: dftSpectrum]].

* **flags** JSON array of strings representing bits to be OR'd: `DFT_SCALE`, `DFT_INVERSE`, `DFT_COMPLEX_OUTPUT`, `DFT_REAL_OUTPUT`. 

#### Model
<pre>{}</pre>

#### Example: DFT of white rectangle [pipeline](https://github.com/firepick1/FireSight/blob/master/json/dft-rect2.json)
<pre>firesight -i img/whiterect.jpg -p json/dft-spectrum.json -o target/dft-rect.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true">&nbsp;&nbsp;&nbsp;<img src="https://github.com/firepick1/FireSight/blob/master/img/dft-rect.jpg?raw=true">

#### Example: [White rectangle](https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true) DFT and inverse DFT [pipeline](https://github.com/firepick1/FireSight/blob/master/json/dft.json)

<pre> firesight -i img/whiterect.jpg -p json/dft.json -o target/dft.jpg</pre>

Demonstrates that the input/output images are identical after being passed through:
* forward DFT:
<pre>
({"flags": ["DFT_SCALE", "DFT_COMPLEX_OUTPUT"], "op": "dft", "comment": "Compute DFT of image"}
</pre>
* inverse DFT:
<pre>
{"flags": ["DFT_INVERSE", "DFT_REAL_OUTPUT"], "op": "dft", "comment": "Compute inverse DFT to restore image"}
</pre>

#### See Also
[[op: dftSpectrum]]

