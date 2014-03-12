These instructions have been tested using:
* Windows 7 Professional SP1; CMake 2.8.12.2
* Visual Studio C++ Express 2010

#### Prerequisites: FireSight source
1. [Install git version 1.9.0 or later](http://git-scm.com/download/win)
1. Open a CMD prompt and cd to the root directory that will contain your FireSight project
1. `git clone https://github.com/firepick1/FireSight`

#### Prerequisites: OpenCV
1. [Install OpenCV 2.4.8 pre-built Libraries for Windows](http://docs.opencv.org/doc/tutorials/introduction/windows_install/windows_install.html). Take care to specify the correct value for _OPENCV_DIR_. For example, your system may be on C: instead of D:. Also be sure to choose the **x86 32-bit libraries** for OpenCV unless CMake says you have a 64-bit machine.
1. Verify installation by typing `opencv_performance` and you should see:
<pre>
Usage: opencv_performance
  -data <classifier_directory_name>
  -info <collection_file_name>
  [-maxSizeDiff <max_size_difference = 1.500000>]
  [-maxPosDiff <max_position_difference = 0.300000>]
  [-sf <scale_factor = 1.200000>]
  [-ni]
  [-nos <number_of_stages = -1>]
  [-rs <roc_size = 40>]
  [-w <sample_width = 24>]
  [-h <sample_height = 24>]
</pre>

#### Prerequisites: Visual C++ 2010 Express
Given the limitations of Windows 8, we recommend Visual Studio 2010 Express, which can run on Windows 7. Visual Studio 2013 requires Windows 8.
1. [Install Visual C++ 2010 Express](http://www.visualstudio.com/en-us/downloads/download-visual-studio-vs#DownloadFamilies_4)
1. [Install Visual Studio 2010 SP1](http://www.microsoft.com/en-us/download/details.aspx?id=23691)

#### Prerequisites: Build Jansson
1. [Install CMake for Windows](http://www.cmake.org/cmake/resources/software.html)
1. From a CMD prompt, `cd` _your-FireSight-directory_
1. `git clone git://github.com/akheron/jansson`
1. Launch CMake to build jansson as a sub-directory of FireSight
1. **Where is the source code:** _your-FireSight-directory_\jansson
1. **Where to build the binaries:** _your-FireSight-directory_\jansson\msvc
1. **File | Delete Cache**
1. **Configure**
1. **Specify the generator for this project** `Visual Studio 10` [Finish]
1. **JANSSON_BUILD_DOCS** `[ ]`
1. **JANSSON_BUILD_SHARED_LIBS** `[X]`
1. **Configure**
1. **Generate** to create _msvc\jansson.sln_
1. From a CMD prompt, cd to your FireSight directory
1. `jansson\msvc\jansson.sln`
1. `F7` to Build Solution
1. Confirm that build created **jansson\msvc\bin\Debug\jansson_d.dll**

#### Prerequisites: Create FireSight MSVC solution
1. Launch CMake
1. **Where is the source code:** _your-FireSight-directory_
1. **Where to build the binaries:** _your-FireSight-directory_\msvc`
1. **File | Delete Cache**
1. **Configure**
1. **Specify the generator for this project** `Visual Studio 10` [Finish]
1. **Generate** to create _msvc\firesight.sln_

#### Build FireSight
1. Launch Visual C++ 2010 Express
1. **Open Project** Locate your FireSight folder and open msvc\firesight.sln_
1. Right click _solution 'firesight' (8 projects)_ and **Rebuild Solution**
1. Open CMD prompt in FireSight directory
1. `target\firesight.exe -i img\pcb.jpg -p json\matchAngle.json -Dtemplate=img\tmplt-37x29.jpg -o target\matchAngle.jpg`
1. Look at `target\matchAngle.jpg` and you should see this:
<img src="https://github.com/firepick1/FireSight/blob/master/img/matchCCOEFF_NORMED-input.jpg?raw=true">

#### Debug FireSight
1. Launch Visual C++ 2010 Express
1. **Open Project** Locate your FireSight folder and open msvc\firesight.sln_
1. **Tools|Options|Debugging|Output Window|Module Load Messages** `Off` 
1. Right click _firesight_ project (the third project, not the first one)_ and **Set as Startup Project**
1. Right click _firesight_ project and choose **Properties**
1. Select **Debuggging**
1. **Command** `$(MSBuildProjectDirectory)\..\target\firesight.exe`
1. **Command Arguments** `-i img\pcb.jpg -p json\matchAngle.json -Dtemplate=img\tmplt-37x29.jpg -o target\matchAngle.jpg`
1. **Working Directory** `$(MSBuildProjectDirectory)\..`
1. `OK` to exit Properties dialog
1. `F10` to step into main()

#### See Also
* [[Build FireSight (Linux)]]
