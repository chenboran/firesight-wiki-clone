Detect and decode text QR codes.

<a href="https://github.com/firepick1/FirePick/wiki/LGPL-Restricted"><img src="https://raw.githubusercontent.com/wiki/firepick1/FirePick/LGPL-restricted.jpg"</img></a>

This stage uses the zbar library (http://zbar.sourceforge.net/).

#### Pipeline
<pre> {"op":"qrDecode", "show":1}</pre>
* **show** update working image and
 `0`:do not show detected QR codes; 
 `1`:show boundaries of detected QR codes; 

#### Results

The output of the stage is an array of qr code center coordinates and decoded text. If the qr code is not decoded (or not present in the image), both the coordinates default to -1.

Running the following command
<pre>firesight -p json/qrDecode.json -i 600px-QR_Code_Damaged.jpg -o qr-damaged-result.jpg</pre>
on an <a href=https://en.wikipedia.org/wiki/File:QR_Code_Damaged.jpg>image</a> taken from Wikipedia yields the following results:
<pre>{
  "s1":{
    "qrdata":[
      {
        "x":304.0,
        "y":292.0,
        "text":"http://en.m.wikipedia.org"
      }
    ]
  }
}</pre>

![qr-damaged-result](img/qr-damaged-result.jpg)
