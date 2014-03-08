Set working image to contents of given file using [imread](http://docs.opencv.org/modules/highgui/doc/reading_and_writing_images_and_video.html?highlight=imread#imread) 

#### Example
<pre>
{ "op":"imread", "path":"cam.jpg" }
</pre>

* **path** image file path

#### Model
<pre>
  { "cols":800, "rows":200 }
</pre>

* **cols** image pixel width
* **rows** image pixel height

#### See Also
* [[op imwrite]]
