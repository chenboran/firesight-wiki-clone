Perform [morphological operation](http://en.wikipedia.org/wiki/Mathematical_morphology). 
_FireSight_ wrapper for:
* [OpenCV erode](http://docs.opencv.org/modules/imgproc/doc/filtering.html?highlight=erode#erode)
* [OpenCV dilate](http://docs.opencv.org/modules/imgproc/doc/filtering.html?highlight=dilate#dilate)
* [OpenCV morphologyEx](http://docs.opencv.org/modules/imgproc/doc/filtering.html?highlight=morphologyex#morphologyex)

Parameters:
* **mop** Default `MORPH_OPEN`. Also `MORPH_CLOSE`, `MORPH_DILATE`, `MORPH_ERODE`, `MORPH_GRADIENT`, `MORPH_TOPHAT`, `MORPH_BLACKHAT`
* **ksize** JSON [width,height] array or integer giving kernel size. Default `3`
* **shape** Default `MORPH_ELLIPSE`. Also `MORPH_RECT` and `MORPH_CROSS`.

#### Stage Model
<pre>{}</pre>

### Example 1: Create test image [pipeline](https://github.com/firepick1/FireSight/blob/master/json/w.json)
<pre>firesight -p json/w.json -o target/w.png</pre>
<img src="https://github.com/firepick1/FireSight/blob/master/img/w.png?raw=true">

### Example 2: MORPH_ERODE [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_ERODE -Dksize=3 -o target/morph-erode-3.png</pre>
| [[Pixel]]:1.7ms [[SOS]]:2ms [[RPi]]:229ms 

Extend black.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-erode-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-erode-5.png?raw=true">
</td></tr>
</table>

### Example 3: MORPH_DILATE [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_DILATE -Dksize=3 -o target/morph-dilate-3.png</pre>
| [[Pixel]]:1.7ms [[SOS]]:2ms [[RPi]]:229ms 

Extend white.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-dilate-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-dilate-5.png?raw=true">
</td></tr>
</table>


### Example 4: MORPH_OPEN [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_OPEN -Dksize=3 -o target/morph-open-3.png</pre>
| [[Pixel]]:3.1ms [[SOS]]:4.7ms [[RPi]]:454ms 

Eliminate white spots.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-open-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-open-5.png?raw=true">
</td></tr>
</table>


### Example 5: MORPH_CLOSE [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_CLOSE -Dksize=3 -o target/morph-close-3.png</pre>
| [[Pixel]]:3.1ms [[SOS]]:4.7ms [[RPi]]:454ms 

Eliminate black spots.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-close-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-close-5.png?raw=true">
</td></tr>
</table>

### Example 6: MORPH_GRADIENT [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_GRADIENT -Dksize=3 -o target/morph-gradient-3.png</pre>
| [[Pixel]]:3.7ms [[SOS]]:4.3ms [[RPi]]:526ms 

Highlight contours.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-gradient-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-gradient-5.png?raw=true">
</td></tr>
</table>

### Example 7: MORPH_TOPHAT [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_TOPHAT -Dksize=3 -o target/morph-tophat-3.png</pre>
| [[Pixel]]:3.7ms [[SOS]]:4.3ms [[RPi]]:526ms 

Highlight local maxima.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-tophat-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-tophat-5.png?raw=true">
</td></tr>
</table>

### Example 8: MORPH_BLACKHAT [pipeline](https://github.com/firepick1/FireSight/blob/master/json/morph.json)
<pre>firesight -i img/w.png -p json/morph.json -Dmop=MORPH_BLACKHAT -Dksize=3 -o target/morph-blackhat-3.png</pre>
| [[Pixel]]:3.7ms [[SOS]]:4.3ms [[RPi]]:526ms 

Highlight local minima.
<table>
<tr><th>ksize=3</th><th>ksize=5</th></tr>
<tr><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-blackhat-3.png?raw=true">
</td><td>
<img src="https://github.com/firepick1/FireSight/blob/master/img/morph-blackhat-5.png?raw=true">
</td></tr>
</table>

