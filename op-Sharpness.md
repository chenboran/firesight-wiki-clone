Estimate 'sharpness' of an input image. See [fpd-vision XP005](https://github.com/firepick1/fpd-vision/tree/master/XP005-focal-range) for more information

#### Pipeline
<pre> {"op":"sharpness", "method":"GRAS"}</pre>
* **method** which method to use

#### Stage Model
<pre>
{
  "s1":{
    "sharpness":13.503684210526316
  }
}
</pre>
* **sharpness** computed sharpness

#### Example with GRAS method
<pre>firesight -i img/cam.jpg -p json/sharpness.json</pre>
<pre>
  "s1":{
    "sharpness":6.0882352941176467
  }
</pre>