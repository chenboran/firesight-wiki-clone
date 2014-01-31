You can use the FireSight C++ shared library, `lib_firesight.so`, to build your own application.

* See [FireSight.cpp](https://github.com/firepick1/FireSight/blob/master/FireSight.cpp) for an example of calling the shared library
* See [CMakeLists.txt](https://github.com/firepick1/FireSight/blob/master/CMakeLists.txt) for an example of how to build an application that uses the shared library

#### Example (process)
To use FireSight as a library, first specify a pipeline:
<pre>char *pPipelineStr = provideYourOwnJsonPipelineString();</pre>

Then create a simple Pipeline with a JSON string
<pre>Pipeline pipeline(pPipelineStr);</pre>

Call the pipeline to process the image
<pre>json_t *pModel = pipeline.process(image);</pre>

When you're done with it, free the returned model!
<pre>json_decref(pModel)</pre>
