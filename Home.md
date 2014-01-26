[FireSight](https://github.com/firepick1/FireSight/blob/master/README.md) interprets the JSON specification of an image processing pipeline and generates a corresponding JSON model of the recognized features for use by other applications. FireSight is available as:

* **libfiresight.so** a C++ shared library
* **firesight** a UNIX executable

Using JSON for specifying the pipeline has certain advantages:
* a simple text editor lets a user experiment with a useful subset of OpenCV
* applications can easily create dynamic image processing pipelines in response to changing user needs

### Pipeline Stages 
Pipeline stages can be named. If the "name" field is omitted, stages are named in sequence: s1, s2, etc. Stage operation is defined by the "op" field:
* [[op: blur]]
* [[op: Canny]]
* [[op: cvtColor]]
* [[op: dilate]]
* [[op: erode]]
* [[op: HoleRecognizer]]
* [[op: imread]]
* [[op: imwrite]]
