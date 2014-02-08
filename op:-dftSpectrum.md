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

Here's the output, which shows how the spectrum is massaged into a JPG that a human can understand:
<pre>
CV_32FC2(400x400) show:[0-9,0-9] Complex spectrum, real part
  7.5  -7.3   6.8  -6.0   5.0  -3.8   2.6  -1.4   0.3   0.5
 -6.8   6.6  -6.2   5.4  -4.5   3.4  -2.3   1.2  -0.3  -0.5
  4.9  -4.8   4.4  -3.9   3.2  -2.5   1.7  -0.9   0.2   0.4
 -2.4   2.3  -2.2   1.9  -1.6   1.2  -0.8   0.4  -0.1  -0.2
  0.2  -0.1   0.1  -0.1   0.1  -0.1   0.1  -0.0   0.0   0.0
  1.3  -1.2   1.1  -1.0   0.8  -0.6   0.4  -0.2   0.1   0.1
 -1.6   1.6  -1.5   1.3  -1.1   0.8  -0.5   0.3  -0.1  -0.1
  1.1  -1.1   1.0  -0.9   0.7  -0.5   0.4  -0.2   0.0   0.1
 -0.2   0.1  -0.1   0.1  -0.1   0.1  -0.1   0.0  -0.0  -0.0
 -0.6   0.6  -0.6   0.5  -0.4   0.3  -0.2   0.1  -0.0  -0.0
CV_32FC2(400x400) show:[0-9,0-9] Complex spectrum, imaginary part
  0.0  -0.1   0.1  -0.1   0.2  -0.1   0.1  -0.1   0.0   0.0
 -0.1   0.1  -0.1   0.2  -0.2   0.2  -0.1   0.1  -0.0  -0.0
  0.1  -0.1   0.1  -0.2   0.2  -0.1   0.1  -0.1   0.0   0.0
 -0.1   0.1  -0.1   0.1  -0.1   0.1  -0.1   0.0  -0.0  -0.0
  0.0  -0.0   0.0  -0.0   0.0  -0.0   0.0  -0.0   0.0   0.0
  0.0  -0.1   0.1  -0.1   0.1  -0.1   0.0  -0.0   0.0   0.0
 -0.1   0.1  -0.1   0.1  -0.1   0.1  -0.1   0.0  -0.0  -0.0
  0.1  -0.1   0.1  -0.1   0.1  -0.1   0.0  -0.0   0.0   0.0
 -0.0   0.0  -0.0   0.0  -0.0   0.0  -0.0   0.0  -0.0  -0.0
 -0.0   0.0  -0.1   0.0  -0.0   0.0  -0.0   0.0  -0.0  -0.0
CV_32FC1(400x400) show:[0-9,0-9] Spectrum magnitude
  2.1   2.1   2.1   1.9   1.8   1.6   1.3   0.9   0.3   0.4
  2.1   2.0   2.0   1.9   1.7   1.5   1.2   0.8   0.2   0.4
  1.8   1.7   1.7   1.6   1.4   1.2   1.0   0.6   0.2   0.3
  1.2   1.2   1.2   1.1   1.0   0.8   0.6   0.4   0.1   0.2
  0.1   0.1   0.1   0.1   0.1   0.1   0.1   0.0   0.0   0.0
  0.8   0.8   0.8   0.7   0.6   0.5   0.4   0.2   0.1   0.1
  1.0   0.9   0.9   0.8   0.7   0.6   0.4   0.3   0.1   0.1
  0.7   0.7   0.7   0.6   0.5   0.4   0.3   0.2   0.0   0.1
  0.1   0.1   0.1   0.1   0.1   0.1   0.1   0.0   0.0   0.0
  0.5   0.5   0.5   0.4   0.4   0.3   0.2   0.1   0.0   0.0
CV_32FC1(400x400) show:[195-204,195-204] Centered spectrum
 0.00  0.00  0.00  0.00  0.00  0.82  0.80  0.76  0.70  0.61
 0.00  0.00  0.00  0.00  0.00  0.14  0.14  0.13  0.12  0.10
 0.00  0.00  0.00  0.00  0.00  1.22  1.21  1.16  1.07  0.95
 0.00  0.00  0.00  0.00  0.00  1.77  1.75  1.69  1.59  1.44
 0.00  0.00  0.00  0.00  0.00  2.05  2.03  1.97  1.86  1.70
 0.00  0.00  0.00  0.00  0.00  2.14  2.12  2.06  1.95  1.79
 0.00  0.00  0.00  0.00  0.00  2.05  2.03  1.97  1.86  1.70
 0.00  0.00  0.00  0.00  0.00  1.77  1.75  1.69  1.59  1.44
 0.00  0.00  0.00  0.00  0.00  1.22  1.21  1.16  1.07  0.95
 0.00  0.00  0.00  0.00  0.00  0.14  0.14  0.13  0.12  0.10
CV_32FC1(400x400) show:[195-204,195-204] Mirrored spectrum
 0.61  0.70  0.76  0.80  0.82  0.82  0.80  0.76  0.70  0.61
 0.10  0.12  0.13  0.14  0.14  0.14  0.14  0.13  0.12  0.10
 0.95  1.07  1.16  1.21  1.22  1.22  1.21  1.16  1.07  0.95
 1.44  1.59  1.69  1.75  1.77  1.77  1.75  1.69  1.59  1.44
 1.70  1.86  1.97  2.03  2.05  2.05  2.03  1.97  1.86  1.70
 1.79  1.95  2.06  2.12  2.14  2.14  2.12  2.06  1.95  1.79
 1.70  1.86  1.97  2.03  2.05  2.05  2.03  1.97  1.86  1.70
 1.44  1.59  1.69  1.75  1.77  1.77  1.75  1.69  1.59  1.44
 0.95  1.07  1.16  1.21  1.22  1.22  1.21  1.16  1.07  0.95
 0.10  0.12  0.13  0.14  0.14  0.14  0.14  0.13  0.12  0.10
CV_8UC1(400x400) show:[195-204,195-204] Normalized spectrum
  255   255   255   255   255   255   255   255   255   255
   92   110   124   133   136   136   133   124   110    92
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
  255   255   255   255   255   255   255   255   255   255
   92   110   124   133   136   136   133   124   110    92
</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/whiterect.jpg?raw=true">

<img src="https://github.com/firepick1/FireSight/blob/master/img/dft-rect.jpg?raw=true">

#### See Also
[[op: dft]]
