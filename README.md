#INSTALLATION

Follow these steps, to install and set up all dependencies for the project

##1. Install commands for all dependencies:
```{r, engine='sh', count_lines}

#general dependencies
sudo apt-get update && sudo apt-get upgrade && sudo rpi-update

sudo apt-get install build-essential

sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

sudo apt-get install python-dev python-numpy libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

#OpenCV
git clone https://github.com/Itseez/opencv.git

git clone https://github.com/Itseez/opencv_contrib.git

cd opencv

mkdir build

cd build

cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local \
 -D INSTALL_PYTHON_EXAMPLES=ON \
 -D INSTALL_C_EXAMPLES=OFF \
 -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
 -D BUILD_EXAMPLES=ON ..

make -j $(nproc)

sudo /bin/bash -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'

sudo make install && sudo ldconfig

# BOOST dependencies
sudo apt-get install libboost-system-dev libboost-thread-dev libboost-timer-dev libboost-chrono-dev libboost-filesystem-dev

# WiringPi
git clone git://git.drogon.net/wiringPi
cd wiringPi
./build 
```

##2. Additional Steps:

copy FindWiringPi.cmake to /usr/share/cmake-x.x/Modules

#BUILDING THE PROJECT

To build the project, clone this repository and use one of the provided build scripts to build the project:
###1. If you just want the normal linux build, just use this script:
```{r, engine='sh', count_lines}
./build.sh
```
###2. If you are using OSX and want to code with Xcode, use this script:
```{r, engine='sh', count_lines}
./build_Xcode.sh
```

