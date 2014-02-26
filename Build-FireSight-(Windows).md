#### Prerequisites
1. [Install git version 1.9.0 or later](http://git-scm.com/download/win)
1. [Install OpenCV Pre-build Libraries for Windows](http://docs.opencv.org/doc/tutorials/introduction/windows_install/windows_install.html). These instructions were tested with OpenCV 2.4.8
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

#### Build FireSight
1. Open a CMD prompt and cd to the root directory that will contain your FireSight project
1. `git clone https://github.com/firepick1/FireSight`
1. `git subtree add --squash --prefix=cmake git://github.com/rpavlik/cmake-modules.git master`