The `undistort` stage gives you access to 
[OpenCV undistort](
http://docs.opencv.org/modules/imgproc/doc/geometric_transformations.html#undistort),
which allows you to apply the intrinsic camera matrix and distortion coefficients
returned by 
[OpenCV calibrateCamera](http://docs.opencv.org/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#calibratecamera). The intrinsic camera matrix and distortion coefficients can be:

1. Specified in the _undistort_ stage itself
1. Computed and obtained from a preceding camera calibration stage (see [[op-matchGrid]]).
1. Provided externally as FireSight pipeline arguments

* **cameraMatrix** JSON array [v11,v12,v13,v21,v22,v23,v31,v32.v33] representing a 3x3 cameraMatrix. Default is `[1,0,0,0,1,0,0,0,1]`
* **distCoeffs** JSON array of 4,5, or 8 radial/tangential distortion coefficients. Default is `[]`.
* **model** Name of stage whose model has a JSON "calibrate" object having _cameraMatrix_ and _distCoeffs_.

#### Stage Model
<pre>
{}
</pre>

#### Example: Cutting-corners calibration [pipeline](https://github.com/firepick1/FireSight/blob/master/json/matchGrid.json)
<pre>firesight -i img/cal-grid.jpg -Djson/matchGrid.json -Dtemplate=img/cross32.png -Dcalibrate=ellipse -Dscale=[0.85,0.85]</pre>
If the corners are never used, then ignore them for calibration:

**Distorted image**<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/cal-grid.png?raw=true">

**Undistorted image**<br>
<img src="https://github.com/firepick1/FireSight/blob/master/img/grid-ellipse-85.jpg?raw=true">

