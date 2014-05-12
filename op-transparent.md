_FireSight_ _transparent_ adds an alpha channel to the pipeline image.
If a background color is specified, _transparent_ assigns foreground/background alpha values.

* **bgcolor** JSON array with [B,G,R] background color. Default is `[]`, which treats entire image as foreground
* **alphafg** Normalized value between 0 and 1.0 for foreground alpha channel value.
* **alphabg** Normalized value between 0 and 1.0 for background alpha channel value.
* **roi** JSON array with [x,y,width,height] rectangle describing region of interest.

#### Stage Model
Here is a sample 3-channel _calcOffset_ JSON model:
<pre>{}</pre>

### Example 1: Transparent Logo [pipeline](https://github.com/firepick1/FireSight/blob/master/json/transparent.json)
<pre>firesight -i img/FireREST.png -p json/transparent.json -o target/transparent.png -Dalphafg=.7 -Dalphabg=.3 -Dbgcolor=[255,255,255] -Droi=[50,10,100,46]</pre>
> [[Pixel]]:0.8ms

Consider a color image with a white background:

<img src="https://github.com/firepick1/FireSight/blob/master/img/FireREST.png?raw=true">

FireSight gives us the following transparent image:

<img src="https://github.com/firepick1/FireSight/blob/master/img/transparent.png?raw=true">
