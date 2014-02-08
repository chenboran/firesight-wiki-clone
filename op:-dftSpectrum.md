The _FireSight_ `dftSpectrum` pipeline stage wraps several OpenCV calls that help you visualize a Fourier transform.

* **delta** A value to add to all elements of the spectrum. Normally used in conjunction with `log` to ensure that all values are positive. Default is `1`
* **shift** Default is `true`, which shifts the Fourier spectrum from the top left corner to the center of the Mat.
* **mirror** Default is `true`, which mirrors the shifted spectrum across the y-axis for the negative frequency portion of the spectrum.
* **log** Default is `true`, which replaces each Mat value with its logarithm to decrease the dynamic range of the spectrum for easier visualization.
* **show** `magnitude` (Default) Replaces working image with the CV_32F1 magnitude of the complex spectrum
* **show** `phase` Replaces working image with the CV_32F1 phase of the complex spectrum
* **show** `real` Replaces working image with the CV_32F1 real part of the complex spectrum
* **show** `imaginary` Replaces working image with the CV_32F1 imaginary part of the complex spectrum

#### Model
<pre>{}</pre>

#### Examples

##### DFT of white rectangle [pipeline](https://github.com/firepick1/FireSight/blob/master/json/dft-rect2.json)
<pre>firesight -p json/dft-rect.json -o target/dft-rect.jpg</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true">

<img src="https://github.com/firepick1/FireSight/blob/master/img/dft-rect.jpg?raw=true">

#### See Also
[[op: dft]]
