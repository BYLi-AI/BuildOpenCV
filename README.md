# BuildOpenCV

Build OpenCV from source

## 1. Prepare system

Update package cache and upgrade<br/>
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

Build tools<br/>
```bash
$ sudo apt-get install build-essential cmake unzip pkg-config
```

Video and image IO libraries<br/>
```bash
$ sudo apt-get install libjpeg-dev libpng-dev libtiff-dev
$ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
$ sudo apt-get install libxvidcore-dev libx264-dev
```

GUI backend<br/>
```bash
$ sudo apt-get install libgtk-3-dev
```

Followed by installing two packages which contain mathematical optimizations for OpenCV:
```bash
$ sudo apt-get install libatlas-base-dev gfortran
```

Install the Python 3 development headers:
```bash
$ sudo apt-get install python3-dev
```

Download OpenCV
```bash
$ cd ~
$ wget -O opencv.zip https://github.com/opencv/opencv/archive/4.0.0.zip
$ wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.0.0.zip
```

unzip the archives:
```bash
$ unzip opencv.zip
$ unzip opencv_contrib.zip
```

## 2. CMake and compile OpenCV
First create build folder
```bash
$ cd ~/opencv
$ mkdir build
$ cd build
```

Prepare CMake run options: <br/>
Reference [link](https://docs.opencv.org/master/db/d05/tutorial_config_reference.html):
```
-D CMAKE_BUILD_TYPE=RELEASE             --> release build
-D CMAKE_INSTALL_PREFIX=/usr/local      --> can input optional location ~/opencv/install
-D OPENCV_ENABLE_NONFREE=OFF            -->  disable Non-free functions
-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules --> Path to opencv contrib module
-D PYTHON_EXECUTABLE=/usr/bin/python    --> path to your python
```

Create optional installation directory<br/>
```bash
$ mkdir ~/opencv_install
```

CMake build command:<br/>

```bash
$ cmake -D CMAKE_BUILD_TYPE=RELEASE \
	-D CMAKE_INSTALL_PREFIX=~/opencv_install \
	-D OPENCV_ENABLE_NONFREE=OFF \
	-D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
	-D PYTHON_EXECUTABLE=/usr/bin/python \
	..
```

Verify output of CMake and Install <br/>
```
$ sudo make install
$ sudo ldconfig
```


## Reference
[OpenCV Official Guide](https://docs.opencv.org/4.5.3/df/d65/tutorial_table_of_content_introduction.html) <br/>

[CMake configuration options](https://docs.opencv.org/4.5.3/d7/d9f/tutorial_linux_install.html) <br/>
