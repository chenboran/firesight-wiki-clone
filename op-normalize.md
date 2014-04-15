Mathematically, normalization scales the intensity of image pixels relative to a given normalization value and type. Normalization provides a valuable standard of comparison and is implemented by [OpenCV normalize](http://docs.opencv.org/modules/core/doc/operations_on_arrays.html#normalize).

Normalization can also be used for contrast shifting and scaling to focus on "pixel values of interest" and is a great visual aid for analyzing images. _FireSight_ extends OpenCV with a _domain_ parameter that lets you choose a range of pixel intensities of interest (see Example 3).

* **alpha** Norm value to normalize to or the lower range boundary in case of the range normalization. Default is `1` unless image is 8-bit, in which case _FireSight_ will automatically compute a good value.
* **beta** Upper range boundary in case of the range normalization; it is not used for the norm normalization. Only used for NORM_MINMAX.
* **normType** normalization type ([NORM_L2](http://mathworld.wolfram.com/L2-Norm.html) (default), [NORM_L1](http://mathworld.wolfram.com/L1-Norm.html), NORM_MINMAX, [NORM_INF](http://mathworld.wolfram.com/L-Infinity-Norm.html)).

For 8-bit images, _FireSight_ provides two parameters which are much more convenient to use than _alpha_ and _beta_:

* **domain** JSON array of integers describing value interval to normalize. Default is `[0,255]`. Values outside this interval will be eliminated from pipeline image by truncating and shifting image values. This works for all normalization types and is useful for focusing on a value interval of interest.
* **range** JSON array of integers describing output value interval. Default is `[0,255]`, which maximizes the dynamic range of the normalized output. This is rarely used.

#### Model
<pre>{}</pre>

#### Examples
The examples below use the following test image. 
The test image has pixel values in the range [0,255] with a background pixel value of 32.  
Within the test image are letters in the grayscale range [20,52].
The letters are difficult to see with the naked eye:

<img src="https://github.com/firepick1/FireSight/blob/master/img/abc.png?raw=true">

#### Example 1: Show ABC [pipeline](https://github.com/firepick1/FireSight/blob/master/json/normalize.json)
<pre>firesight -i img/abc.png -p json/normalize.json -o target/normalize.png</pre>
> [[Pixel]]:0.6ms [[RPi]]:11ms

The default NORM_L2 normalization reveals the letters hidden in the test image.

<img src="https://github.com/firepick1/FireSight/blob/master/img/normalize.png?raw=true">

#### Example 2: High Contrast ABC [pipeline](https://github.com/firepick1/FireSight/blob/master/json/normalize.json)
<pre>firesight -i img/abc.png -p json/normalize.json -o target/normalize.png -Ddomain=[20,52]</pre>
> [[Pixel]]:0.8ms [[RPi]]:14ms

By choosing a _domain_ that matches the values used to represent the letters, we eliminate uninteresting dark/light values.
This allows us to increase the image gain and bias it toward the value interval of interest:

<img src="https://github.com/firepick1/FireSight/blob/master/img/normalize-l2.png?raw=true">

#### See Also
* [[op absdiff]]
* [[op threshold]]

#### Example 3: normType and domain
The following table illustrates the utility of the various normType options. 
It also shows how the domain interval can improve contrast.
<table>
<tr>
<th>&nbsp;</th>
<th colspan=2> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34.png?raw=true"> </th>
<th colspan=2> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182.png?raw=true"> </th>
</tr>
<tr>
<th>normType</th>
<th>no domain</th><th>domain=[20,52]</th>
<th>no domain</th><th>domain=[164,196]</th>
</tr>

<tr>
<td>NORM_MINMAX</td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-minmax.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-minmax-dom.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-minmax.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-minmax-dom.png?raw=true"> </td>
</tr>

<tr>
<td>NORM_INF</td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-inf.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-inf-dom.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-inf.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-inf-dom.png?raw=true"> </td>
</tr>

<tr>
<td>NORM_L1</td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-l1.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-l1-dom.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-l1.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-l1-dom.png?raw=true"> </td>
</tr>

<tr>
<td>NORM_L2</td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-l2.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc34-l2-dom.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-l2.png?raw=true"> </td>
<td> <img src="https://github.com/firepick1/FireSight/blob/master/img/abc182-l2-dom.png?raw=true"> </td>
</tr>

</table>
