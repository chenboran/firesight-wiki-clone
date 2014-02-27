If you find yourself creating many pipelines that only differ by a few simple values, you may want to consider using _pipeline parameters_. A pipeline parameter is a name/value pair with an optional default. Consider the following pipeline to resize an image to 50% of the original size:
<pre>
[
  {"op":"resize", "fx":0.5, "fy":0.5}
]
</pre>

If we want to resize an image by 75%, we could certainly create another pipeline. However, it may be easier to use a pipeline with parameters _{{fx}}_ and _{{fy}}_. Specifically, the caller provides definitions for _fx_ and _fy_, since the braces are parameter delimiters:
<pre>
[
  {"op":"resize", "fx":"{{fx}}", "fy":"{{fy}}"}
]
</pre>

If the caller does NOT provide a parameter's value, then you'll get an error unless you provide a default value using the _||_ delimiter:
<pre>
[
  {"op":"resize", "fx":"{{fx||0.5}}", "fy":"{{fy||0.5}}"}
]</pre>

Pipeline parameter values can be defined using the "-D" option of [[firesight]]:
<pre>firesight -i img/duck.jpg -p json/resize.json -o target/resize.jpg -Dfx=0.25 -Dfy=0.5</pre>

#### JSON Data Types

In the above example, we introduced a parameter for a JSON numeric double value. More precisely, we specified the parameter using a string (e.g., "{{fy||0.5}}"), and a string isn't a JSON number. _FireSight_ handles this by applying the JSON parser to any value with embedded parameter delimiters (i.e., "{{"). Since the string is parsed, we end up with a real JSON object as the replacement. This lets us parameterize a JSON array used to represent a BGR color that defaults to magenta:
<pre>
[
  {"op":"rectangle", "width":"{{width}}", "height":"{{height}}", "color":"{{color||[255,0,255]}}"}
]
</pre>

#### See Also
* [[op: resize]]