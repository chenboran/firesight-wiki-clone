
FireSight `matchGrid` works much like standard chessboard 
[OpenCV Camera Calibration](http://docs.opencv.org/doc/tutorials/calib3d/camera_calibration/camera_calibration.html). 
However, `matchGrid` is designed to for use in pick-and-place camera calibration,
which has slightly different requirements (flat, almost 2D space used for motion planning measurement) 
than standard chessboard calibration (large 3D space used for location/pose detection).

The FireSight `matchGrid` stage matches recognized features from a preceding FireSight stage
to a rectangular grid and computes
camera calibration parameters from matched features. This stage requires a preceding
stage such as [[op-matchTemplate]] to recognize the features to be matched. This separation
allows for free experimentation on what 
constitutes the grid (e.g., holes, diamonds, crosshairs, etc.). Recognized features should
be provided to `matchGrid` via the FireSight model pipeline as a JSON array of rects
such as those returned by [[op-matchTemplate]].

<img src="https://github.com/firepick1/FireSight/blob/master/img/cal-grid.png?raw=true">

OpenCV chessboard calibration requires many images at different chessboard angles, 
chessboard distances and camera angles. For `matchGrid`, the input imaging requirement 
is different, and the calibration grid should be presented to the camera in a 
single Z plane, since that corresponds directly with the pick-and-place use case.
For best results, the presented grid should be aligned with the camera axes
(i.e., avoid random orientations)
FireSight `matchGrid` only requires a single image for calibration, but it can
use sub-images to mimic chessboard calibration.

The method used to match the grid is FireSight specific.

* **sep** JSON [X,Y] array of horizontal (x) and vertical (y) grid separation. Default is `[5,5]` for a 5mm grid
* **calibrate** Default is `best`, which chooses the best known matching algorithm. See **calibrate options**.
* **tolerance** used to match features in a row or column. Default is `0.35`.
* **color** JSON BGR color array to mark unused image features. Default is `[255,255,255]`.
* **scale** JSON [X,Y] array of scaling coefficients for calibration. Currently only used by `ellipse`, default value is `[1,1]`

#### calibrate options
* **best** Use best known option (may change between software versions)
* **tile1** Use all matched grid points in a single calibration image
* **tile2** Use all matched grid points in each image quadrant to make up a set of four calibration images
* **tile3** Use all matched grid points in a 3x3 matrix of 9 calibration images
* **tile4** Use all matched grid points in a 4x4 matrix of 16 calibration images
* **tile5** Use all matched grid points in a 5x5 matrix of 25 calibration images
* **ellipse** Use all matched grid points within a scaled XY ellipse for a single calibration image.
* other experimental options may be available

#### Stage Model
<pre>
{
  ...
  "grid1":{
    "dxMedian":-31.0,
    "dxCount1":119,
    "dxCount2":108,
    "dxdxAvg1":-31.512605667114258,
    "dxdyAvg1":0.81512606143951416,
    "dxdxAvg2":-31.527778625488281,
    "dxdyAvg2":0.81944441795349121,
    "gridX":6.307685375213623,
    "dyMedian":-31.0,
    "dyCount1":117,
    "dyCount2":105,
    "dydxAvg1":-0.76068377494812012,
    "dydyAvg1":-31.24786376953125,
    "dydxAvg2":-0.77142858505249023,
    "dydyAvg2":-31.233333587646484,
    "gridY":6.2485718727111816,
    "rects":[
      {
        "x":21.0,
        "y":37.0,
        "objX":-27.961538314819336,
        "objY":-24.269229888916016
      },
	  ...
      {
        "x":343.0,
        "y":341.0,
        "objX":22.038461685180664,
        "objY":25.730770111083984
      }
    ],
    "calibrate":{
      "op":"tile3",
      "cameraMatrix":[
        1440.1324385220225,
        0.0,
        196.70893717039402,
        0.0,
        1454.3392551157376,
        200.6564634241056,
        0.0,
        0.0,
        1.0
      ],
      "perspective":[
        0.033142981113263262,
        0.0010300462632817817,
        0.27592684208159102,
        0.00082654537237368509,
        0.035259955173039821,
        -0.31193463702077528,
        -1.3832327695672043e-5,
        0.00027923340765282609,
        1.0
      ],
      "distCoeffs":[
        0.77584616408796647,
        -27.648993864449466,
        0.054364941338627917,
        -0.011841923059093425,
        122.75376662043016
      ],
      "candidates":130,
      "matched":130,
      "rmserror":0.38765870207220959,
      "images":9.0,
      "gridnessIn":[
        3.8133699893951416,
        4.2762274742126465
      ],
      "gridnessOut":[
        0.34463158249855042,
        0.37010332942008972
      ]
    }
  },
  ...
}
</pre>
* **gridX** The calculated pixels per grid X-separation unit
* **gridY** The calculated pixels per grid Y-separation unit
* **rects** The RotatedRect values of the matched positions
* **rmserror** The root of the mean squared error returned by OpenCV cameraCalibrate()
* **images** number of sub-images used for calibration
* **candidates** number of matched grid points
* **matched** number of matched grid points actually used as input to OpenCV cameraCalibrate()
* **gridnessIn** RMS point-by-point error of input image with respect to overlaid grid. A perfect grid match is 0.
* **gridnessOut** RMS point-by-point error of output image with respect to overlaid grid. A perfect grid match is 0.

#### Example: Full grid calibration [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid.json)
<pre>firesight -i img/cal-grid.jpg -Djson/matchGrid.json -Dtemplate=img/cross32.png -Dcalibrate=tile1</pre>
Using all the grid points for calibration minimizes overall error:

<img src="https://github.com/firepick1/FireSight/blob/master/img/grid-tile1.jpg?raw=true">

#### Example: Tic-Tac-Tile3 calibration [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid.json)
<pre>firesight -i img/cal-grid.jpg -Djson/matchGrid.json -Dtemplate=img/cross32.png -Dcalibrate=tile3</pre>
Using 9 sub images provides greater local accuracy at the expense of some loss in "the big picture"

<img src="https://github.com/firepick1/FireSight/blob/master/img/grid-tile3.jpg?raw=true">

#### Example: Cutting-corners calibration [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid.json)
<pre>firesight -i img/cal-grid.jpg -Djson/matchGrid.json -Dtemplate=img/cross32.png -Dcalibrate=ellipse -Dscale=[0.85,0.85]</pre>
If the corners are never used, then ignore them for calibration:

<img src="https://github.com/firepick1/FireSight/blob/master/img/grid-ellipse-85.jpg?raw=true">

#### Example: A different perspective [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid-perspective.json)
<pre>firesight -i img/cal-grid.jpg -Djson/matchGrid-perspective.json -Dtemplate=img/cross32.png</pre>
If the imaged objects line on flat surface at an angle with the camera, use _matchGrid_ to determine
the perspective matrix for [warpPerspective](op-warpPerspective). For the image shown below, the RMS gridness
error is about 1/3 of a pixel. In this case, a perspective transformation provides a very usable
cartesian map of the imaged surface _without any calibration._

<pre>
  "perspective":[
	1.0405136564383939,     0.026744906574870872,   -2.943810346145538,
	0.024529984309304427,   1.097007339310166,      -14.050588819421538,
	-1.7780681696463529e-5, 0.00027266213560320576, 1.0
  ],
</pre>

<img src="https://github.com/firepick1/FireSight/blob/master/img/matchGrid-perspective.png?raw=true">
