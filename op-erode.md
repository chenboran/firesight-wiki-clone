# DEPRECATED (see [[op morph]])

OpenCV [erode](http://docs.opencv.org/modules/imgproc/doc/filtering.html?highlight=erode#erode) wrapper. See [overview](http://docs.opencv.org/doc/tutorials/imgproc/erosion_dilatation/erosion_dilatation.html)

* **kwidth** kernel width. Default `3`
* **kheight** kernel height. Default `3`
* **shape** Default `MORPH_ELLIPSE`. Also `MORPH_RECT` and `MORPH_CROSS`.

#### Stage Model
<pre>{}</pre>

### Example 1: 
<pre>firesight -i img/</pre>
<pre>{"op":"erode","ksize.width":3,"ksize.height":3,"shape":"MORPH_ELLIPSE"}</pre>

#### See Also
* [[op dilate]]
