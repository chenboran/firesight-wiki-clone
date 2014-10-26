You can use the FireSight C++ shared library, `lib_firesight.so`, to build your own application.

* See [FireSight.cpp](https://github.com/firepick1/FireSight/blob/master/FireSight.cpp) for an example of calling the shared library
* See [CMakeLists.txt](https://github.com/firepick1/FireSight/blob/master/CMakeLists.txt) for an example of how to build an application that uses the shared library

#### Example (process)
To use FireSight as a library, here is some boilerplate code:
```cpp
#include <FireSight.hpp>
#include <opencv2/core/core.hpp>
#include <opencv2/highgui/highgui.hpp>

using namespace cv;
using namespace firesight;

int main()
{
    //Open an image
    Mat image; // new blank image
    image = cv::imread("test.png", 0);// read the file

    //Create a pipeline
    char *pPipelineStr = "[{\"op\":\"blur\",\"ksize.width\":10,\"ksize.height\":10},{\"op\":\"imwrite\", \"path\":\"blur.jpg\"}]";
    Pipeline pipeline(pPipelineStr);

    //Create an argMap.  Can be empty.
    ArgMap argMap;

    //Process the pipeline
    json_t *pModel = pipeline.process(image, argMap);

    //Release some memory
    json_decref(pModel);

    return 0;
}
```
