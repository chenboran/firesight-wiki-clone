The FireSight shared library is `lib_firesight.so`

* See [FireSight.cpp](https://github.com/firepick1/FireSight/blob/master/FireSight.cpp) for an example of calling the shared library
* See [CMakeLists.txt](https://github.com/firepick1/FireSight/blob/master/CMakeLists.txt) for an example of how to build an application that uses the shared library

To use FireSight as a library, simple create a Pipeline with a JSON string
<pre>Pipeline pipeline(pJsonPipeline);</pre>

Call the pipeline to process the image
<pre>json_t *pModel = pipeline.process(image);</pre>

When you're done with it, free the returned model!
<pre>json_decref(pModel)</pre>
