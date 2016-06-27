INSTALLATION

Install Commands for all dependencies:

sudo apt-get update && sudo apt-get upgrade && sudo rpi-update

sudo apt-get install build-essential

sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev

sudo apt-get install python-dev python-numpy libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev

git clone https://github.com/Itseez/opencv.git

git clone https://github.com/Itseez/opencv_contrib.git

cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local \
 -D INSTALL_PYTHON_EXAMPLES=ON \
 -D INSTALL_C_EXAMPLES=OFF \
 -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
 -D BUILD_EXAMPLES=ON ..

 make -j $(nproc)

 sudo /bin/bash -c 'echo "/usr/local/lib" > /etc/ld.so.conf.d/opencv.conf'

 sudo make install && sudo ldconfig

 sudo apt-get install libboost-system-dev libboost-thread-dev libboost-timer-dev libboost-chrono-dev libboost-filesystem-dev

git clone git://git.drogon.net/wiringPi
cd wiringPi
./build

Additional Steps:

copy FindWiringPi.cmake to /usr/share/cmake-x.x/Modules

