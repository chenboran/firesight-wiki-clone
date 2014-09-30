### UNDER DEVELOPMENT (FUNCTION MAY CHANGE)

Conceptually `matchGrid` works much like standard chessboard 
[[OpenCV Camera Calibration](http://docs.opencv.org/doc/tutorials/calib3d/camera_calibration/camera_calibration.html). However, `matchGrid` is designed to for use in pick-and-place camera calibration,
which has slightly different requirements than standard chessboard calibration.

The FireSight `matchGrid` stage matches recognized features from a preceding FireSight stage
to a rectangular grid and computes
camera calibration parameters from matched features. This stage requires a preceding
stage such as [[op-matchTemplate]] to recognize the features to be matched. This separation
allows for free experimentation on what 
constitutes the grid (e.g., holes, diamonds, crosshairs, etc.). Recognized features should
be provided to `matchGrid` via the FireSight model pipeline as a JSON array of rects
such as those returned by [[op-matchTemplate]].

OpenCV chessboard calibration requires many images at different chessboard angles, 
chessboard distances and camera angles. For `matchGrid`, the input imaging requirement 
is different, and the calibration grid should be presented to the camera in a 
single Z plane, since that corresponds directly with the pick-and-place use case.
For best results, the presented grid should be aligned with the camera axes
(i.e., avoid random orientations)
Currently, only a single image is required, but future versions of `matchGrid` will
support calibration from multiple images.

The method used to match the grid is FireSight specific.

* **sepX** measured grid X separation (printed calibration grids must be measured). Default is `5mm`
* **sepY** measured grid Y separation (printed calibration grids must be measured). Default is `5mm`
* **tolerance** used to match features in a row or column. Default is `0.35`.
* **imageColor** JSON BGR color array to mark image features. Default is `-1` for no marking.
* **objectColor** JSON BGR color array to mark object features. Default is `-1` for no marking.

#### Stage Model
<pre>
{
	"gridX":6.23453423412,
	"gridY":6.23453423412,
    "rects":[
      {
        "x":467.0,
        "y":68.0,
        "width":29.0,
        "height":37.0,
		"color":[255,0,0]
      },
      {
        "x":518.0,
        "y":69.0,
        "width":29.0,
        "height":37.0,
		"color":[255,0,0]
      },
      {
        "x":711.0,
        "y":71.0,
        "width":29.0,
        "height":37.0,
		"color":[255,0,0]
      },
      {
        "x":760.0,
        "y":71.0,
        "width":29.0,
        "height":37.0,
		"color":[255,0,0]
      }
    ]
  }
</pre>
* **gridX** The calculated pixels for grid X-separation
* **gridY** The calculated pixels for grid Y-separation
* **rects** The RotatedRect values of the matched positions
* **x** Center x
* **y** Center y
* **height** Height of rectangle 
* **width** Widht of rectangle

#### Example: TBD [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchCCOEFF_NORMED.json)
<pre>TBD</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/pcb.jpg?raw=true">
