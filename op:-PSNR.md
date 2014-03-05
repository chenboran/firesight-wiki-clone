_FireSight_ stage computes [Peak Signal to Noise Ratio (PSNR)](http://en.wikipedia.org/wiki/Peak_signal-to-noise_ratio). The PSNR is a fast measure of [image similarity](http://docs.opencv.org/doc/tutorials/highgui/video-input-psnr-ssim/video-input-psnr-ssim.html#image-similarity-psnr-and-ssim). The PSNR for similar images is higher than the PSNR for dissimilar images. However the PSNR for identical images is undefined. 

* **threshold** If 0 or greated, the threshold below which images are treated as different. The default of `-1` will only mark identical images as "SAME" in the model.
* **path** Path to reference image to be compared to pipeline image

#### Model
The model stores the PSNR value or "SAME" if the images are found to be similar as defined by _threshold_
<pre>
{
  "PSNR":"SAME"
}
</pre>

#### Example: Compare somewhat similar images [pipeline]()
<pre>target/firesight -i img/pcb.jpg -p json/PSNR.json -Dpath=img/matchAngle.jpg</pre>
pcb.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">

matchAngle.jpg &rarr; <br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchAngle.jpg?raw=true"> 

PSNR value &rarr; <br>
<pre>{ "PSNR":29.65368665440641 }</pre>

Note that the PSNR value is quite close to the 30-50dB range typical for PSNR values deemed acceptable for comparing lossy compressed images with their originals. This demonstrates that differences discernible to humans may not be detected by PSNR. The reason for this is that image difference is highly local (the green rectangles).
