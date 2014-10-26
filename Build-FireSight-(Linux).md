On you Unix, _FireSight_ is built as:
* **[[lib_firesight.so]]** a C++ shared library
* **[[firesight]]** a UNIX command line interface

### Debian, Ubuntu

Linux installation is easy. The following has been tested on :
* Raspbian (Raspberry Pi)
* Ubuntu 12.04 LTS (Chromium Pixel)

<pre>
sudo apt-get install git
git clone git://github.com/firepick1/FireSight
cd FireSight
./build
</pre>

Note: Depending on your distro, you may need to install `build-essential` via the command `sudo apt-get install build-essential`. This was the case for Linux Mint 17 Qiana.  If your build fails with the text: `CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.`, then this means you're missing the g++ compiler, which for some reason doesn't come with the distro.

### Gentoo

Paul Jones has built FireSight on Gentoo.

#### See Also
* [[Build FireSight (Windows)]]
* [[Build FireSight (SmartOS/Solaris)]]
