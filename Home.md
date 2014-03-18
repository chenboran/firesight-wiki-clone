<a href="https://github.com/firepick1/FirePick/wiki/Status"><img src="https://github.com/firepick1/FirePick/wiki/prototype.png"></a>

[FireSight](https://github.com/firepick1/FireSight/blob/master/README.md) interprets a declarative specification of an image processing pipeline that generates a data model of the recognized features for use by other applications. The pipeline declaration and data model both use the JSON data format.

### Pipeline Stages 
Each stage in a pipeline performs a specific operation on the current pipeline image. Pipeline stages can be named. If the "name" field is omitted, stages are named in sequence: s1, s2, etc. Stage operation is defined by the "op" field:
* [[op absdiff]]
* [[op backgroundSubtractor]]
* [[op blur]]
* [[op Canny]]
* [[op cvtColor]]
* [[op dft]]
* [[op dftSpectrum]]
* [[op dilate]]
* [[op drawKeypoints]]
* [[op drawRects]]
* [[op erode]]
* [[op HoleRecognizer]]
* [[op imread]]
* [[op imwrite]]
* [[op matchTemplate]]
* [[op MSER]]
* [[op PSNR]]
* [[op resize]]
* [[op SimpleBlobDetector]]
* [[op warpAffine]]
* [[op warpRing]]

#### See Also
* [[Pipeline Parameters]]
* [[Build FireSight (Linux)]]
* [[Build FireSight (Windows)]]