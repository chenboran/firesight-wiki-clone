Determine the px/mm resolution of the image from a smt tape (4mm separation of holes).

The input to this stage are circles, detected by the [[op HoughCircles]] stage

#### Pipeline
<pre> {"op":"HoughCircles", "diamMin":22.6, "diamMax":29.9, "show":1}</pre>
* **diamMin** minimum diameter in pixels
* **diamMax** maximum diameter in pixels
* **show** update working image and 
 `0`:do not show detected circles; 
 `1`:show detected circles; 

![FireSight - HoughCircles](https://github.com/simonfojtu/FireSight/raw/master/img/HoughCircles.jpg)

#### Stage Model
<pre>
    "circles":[
      {
        "x":404.5,
        "y":49.5,
        "radius":13.209844589233398
      },
      {
        "x":619.5,
        "y":57.5,
        "radius":13.656499862670898
      },
      {
        "x":512.5,
        "y":54.5,
        "radius":12.747549057006836
      },
      {
        "x":191.5,
        "y":43.5,
        "radius":14.159802436828613
      },
      {
        "x":84.5,
        "y":37.5,
        "radius":14.508618354797363
      },
      {
        "x":298.5,
        "y":45.5,
        "radius":13.509256362915039
      }
    ]
</pre>
* **circles** array of JSON objects. each describing a circle
* **x** x coordinate of the circle center [px]
* **y** y coordinate of the circle center [px]
* **radius** radius of the circle [px]

#### Example
<pre>firesight -i img/cam.jpg -p json/HoughCircles.json</pre>
Output image `target/HoughCircles.jpg`