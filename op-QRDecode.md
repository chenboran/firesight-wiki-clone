Detect and decode text QR codes.

<a href="https://github.com/firepick1/FirePick/wiki/LGPL-Restricted"><img src="https://raw.githubusercontent.com/wiki/firepick1/FirePick/LGPL-restricted.jpg"</img></a>

This stage uses the zbar library (http://zbar.sourceforge.net/).

#### Pipeline
<pre> {"op":"qrDecode", "show":1}</pre>
* **show** update working image and
 `0`:do not show detected QR codes; 
 `1`:show boundaries of detected QR codes; 

#### Results

Running the following command
<pre>firesight -p json/qrDecode.json -i 600px-QR_Code_Damaged.jpg -o qr-damaged-result.jpg</pre>
on an image taken from Wikipedia <img src=https://en.wikipedia.org/wiki/File:QR_Code_Damaged.jpg/>
yields the following result.
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
