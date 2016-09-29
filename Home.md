<a href="https://github.com/firepick1/FirePick/wiki/Status"><img src="https://github.com/firepick1/FirePick/wiki/prototype.png"></a>

[FireSight](https://github.com/firepick1/FireSight/blob/master/README.md) interprets a declarative specification of an image processing pipeline that generates a data model of the recognized features for use by other applications. The pipeline declaration and data model both use the JSON data format. Examples shown below all use the [[firesight]] command line application.

### Pipeline Stages 
Each stage in a pipeline performs a specific operation on the current pipeline image. Pipeline stages can be named. If the "name" field is omitted, stages are named in sequence: s1, s2, etc. Stage operation is defined by the "op" field:
* [[op absdiff]] Compare pixel intensities of two images 
* [[op backgroundSubtractor]] Also will run if passed the pipeline name `bgsub`
* [[op blur]]
* [[op calcHist]] Add histogram to pipeline model
* [[op calcOffset]] Calculate offset between two images
* [[op Canny]] Finds edges in an image using the Canny86 algorithm.
* [[op Circle]] Draws a circle
* [[op crop]] Crops pipeline image to rectangle
* [[op cvtColor]] Change image color model
* [[op dft]] Discrete Fourier Transform
* [[op dftSpectrum]] Analyze DFT
* [[op dilate]] Morphological operation.  The background (bright) dilates around the black regions of the letter.
* [[op drawKeypoints]] Visualize key feature points in pipeline model
* [[op drawRects]] Visualize rectangles in pipeline model 
* [[op erode]] Morphological operation.  Bright areas of the image (usually the background) get thinner, whereas the dark zones (the “writing”) gets bigger.
* [[op FireSight]] FireSight configuration 
* [[op HoleRecognizer]]
* [[op HoughCircles]] Circle detector based on Hough transform
* [[op imread]] Read image (multiple formats)
* [[op imwrite]] Write image (multiple formats)
* [[op matchGrid]] Match line intersection points of simple grid
* [[op matchTemplate]] Match all instances of given template image
* [[op meanStdDev]] Find mean and standard deviation of intensities
* [[op minAreaRect]] Find minimum area rectangle enclosing pixels within intensity range
* [[op MSER]] Blob detection
* [[op morph]] Morphological operations
* [[op normalize]] Adjust intensity
* [[op Points2Resolution_RANSAC]]
* [[op PSNR]] Compare two images for similarity using peak signal to noise ratio 
* [[op putText]] Annotate image
* [[op QRDecode]] Decode QR
* [[op rectangle]]
* [[op resize]]
* [[op Sharpness]] Compute 'sharpness' of an image
* [[op SimpleBlobDetector]]
* [[op stageImage]] Replace current pipeline image with previous stage image
* [[op threshold]] Manipulate pixel intensity ranges
* [[op transparent]] Make image transparent by adding an alpha channel
* [[op undistort]] Apply camera calibration to undistort image
* [[op warpAffine]] Scale, translate and/or rotate image
* [[op warpRing]] Create rotation-invariant matching templates
* [[op warpPerspective]] Calculates a perspective transform from four pairs of the corresponding points.

#### See Also
* [[Pipeline Parameters]] Create customizable pipelines
* [[Building Firesight]] Play with or extend FireSight
