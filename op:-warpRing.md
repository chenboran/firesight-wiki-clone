Thos _FireSight_ stage creates recognition templates for different angles using ring projection or a set of specific angles. [Template matching](http://en.wikipedia.org/wiki/Template_matching) is generally sensitive to the angle of the template with respect to the image. However, it is possible to create a rotation-invariant template matching by "stacking and averaging a bunch of rotated templates." A fully rotation-invariant template is created by means of [ring projection](http://www.worldscientific.com/doi/abs/10.1142/S0218001491000053?journalCode=ijprai.

Although rotation invariance is achievable, it comes at a cost. For example, the ring projection of a rectangle template will recognize a "+'or an "X". In other words, there is a tradeoff between rotation-invariance and matching accuracy. One way to address is this is by only using a subset of angles of interest. For example, a [0,90,180,270] multi-angle template will reject an "X" even though it will recognize a "+".

* **angles** JSON array of angles. Default is `[]`, which produces a ring projection of input image.

#### Model
The stage model for _warpRing_ gives the image size of the generated template, which will vary according to the angles specified. A ring projection will always result in a square image:
<pre>
  {
    "width":240,
    "height":240
  }
</pre>

#### Example: 4-way rectangle template  [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchRing-4way.json)
<pre>firesight -i img/rectangle100x162.jpg -p json/warpRing-4way.json -o target/rectangle100x162-4way.jpg</pre>
###### Rectangle template and 4-way template
<img src="https://github.com/firepick1/FireSight/blob/master/img/rectangle100x162.jpg?raw=true">&nbsp;
<img src="https://github.com/firepick1/FireSight/blob/master/img/rectangle100x162-4way.jpg?raw=true">

#### Example: 8-way rectangle template  [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchRing-4way.json)
<pre>firesight -i img/rectangle100x162.jpg -p json/warpRing-8way.json -o target/rectangle100x162-8way.jpg</pre>
###### Rectangle template and 4-way template
<img src="https://github.com/firepick1/FireSight/blob/master/img/rectangle100x162.jpg?raw=true">&nbsp;
<img src="https://github.com/firepick1/FireSight/blob/master/img/rectangle100x162-8way.jpg?raw=true">
