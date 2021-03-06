The **PSNR** _FireSight_ stage computes [Peak Signal to Noise Ratio (PSNR)](http://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio). PSNR is a fast measure of [image similarity](http://docs.opencv.org/doc/tutorials/highgui/video-input-psnr-ssim/video-input-psnr-ssim.html#image-similarity-psnr-and-ssim). The PSNR for similar images is higher than the PSNR for dissimilar images. The PSNR for identical images is undefined in the literature, so _FireSight_ by design returns "SAME". 

* **threshold** If 0 or greater, this specifies the threshold below which images are treated as different. The default of `-1` will only mark identical images as "SAME" in the model.
* **path** Path to reference image to be compared to pipeline image

NOTE: The PSNR stage is used by _FireSight_ itself in unit tests. OpenCV on different platforms transforms images in similar, but not identical ways. The PSNR stage is therefore helpful in comparing, for example, Raspberry Pi FireSight images with Windows FireSight images.

#### Stage Model
The model stores the PSNR value or "SAME" if the images are found to be similar as defined by _threshold_
<pre>
{
  "PSNR":"SAME"
}
</pre>

#### Example 1: Compare somewhat similar images [pipeline](https://github.com/firepick1/FireSight/blob/master/json/PSNR.json)
<pre>firesight -i img/pcb.jpg -p json/PSNR.json -Dpath=img/matchAngle.jpg</pre>
> Pixel: 6ms

pcb.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

matchAngle.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchAngle.jpg?raw=true"> 

PSNR value &rarr; <br>
<pre>{ "PSNR":29.65368665440641 }</pre>

Note that the PSNR value is quite close to the 30-50dB range typical for PSNR values deemed acceptable for comparing lossy compressed images with their originals. This demonstrates that differences discernible to humans may be glossed over by PSNR. The reason for this is that in this case, we have a highly local image difference (i.e., the green rectangles).

#### Example 2: Compare dissimilar images [pipeline](https://github.com/firepick1/FireSight/blob/master/json/PSNR.json)
<pre>firesight -i img/pcb.jpg -p json/PSNR.json -Dpath=img/matchCCORR_NORMED.jpg</pre>
> Pixel: 6ms

pcb.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

matchCCORR_NORMED.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchCCORR_NORMED.jpg?raw=true"> 

PSNR value &rarr; <br>
<pre>{ "PSNR":15.855542323067283 }</pre>

In this case, the PSNR indicates some similarity, but the PSNR is low enough to indicate that these images are different.

#### Example 3: Compare seemingly identical images [pipeline](https://github.com/firepick1/FireSight/blob/master/json/PSNR.json)
<pre>firesight -i img/matchAngle-64.png -p json/PSNR.json -Dpath=img/matchAngle.jpg</pre>
> Pixel: 6ms

The following images were generated on different platforms running different versions of OpenCV. What's interesting about these pictures is that they look the same to the human eye. However, PSNR detects a slight difference.

matchAngle-64.png &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchAngle-64.png?raw=true">

matchAngle.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchAngle.jpg?raw=true"> 

PSNR value &rarr; <br>
<pre>{ "PSNR":36.764313895181303 }</pre>

Images seen as identical can have PSNR values as low as 36.8dB.

