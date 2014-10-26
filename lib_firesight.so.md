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
    Mat image; // new blank image
    image = cv::imread("test.png", 0);// read the file

    char *pPipelineStr = "[{\"op\":\"blur\",\"ksize.width\":10,\"ksize.height\":10},{\"op\":\"imwrite\", \"path\":\"blur.jpg\"}]";
    printf("Input json: \n%s\n\n\n", pPipelineStr);
    Pipeline pipeline(pPipelineStr);
    ArgMap argMap;

    json_t *pModel = pipeline.process(image, argMap);

    // Print out returned model
    char *pModelStr = json_dumps(pModel, JSON_PRESERVE_ORDER|JSON_COMPACT|JSON_INDENT(2));
    printf("%s\n", pModelStr);

    //Release some memory
    free(pModelStr);
    json_decref(pModel);

    //the 'Mat image' has been modified to show the output image.  Display to screen for debug.
    namedWindow( "Display window", CV_WINDOW_AUTOSIZE );// create a window for display.
    imshow( "Display window", image );// show our image inside it.
    waitKey(0);
    return 0;
}
```
