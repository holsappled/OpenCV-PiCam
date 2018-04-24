# OpenCV-PiCam
Using OpenCV with Raspberry Pi 3 utilizing PiCamera Kuman model #SC09-US

https://www.pyimagesearch.com/2015/02/23/install-opencv-and-python-on-your-raspberry-pi-2-and-b/

https://www.pyimagesearch.com/2015/03/30/accessing-the-raspberry-pi-camera-with-opencv-and-python/




Equpiment

1)MicroSD card with OS Raspbian (Not NOOBS)
2)Raspberry Pi 3
3)PiCamera Kuman model #SC09-US
https://www.amazon.com/gp/product/B06XKLLT6G/ref=oh_aui_search_detailpage?ie=UTF8&psc=1






########################

Update and Install OpenCV, Python3... etc.

https://www.pyimagesearch.com/2015/02/23/install-opencv-and-python-on-your-raspberry-pi-2-and-b/


sudo apt-get update
sudo apt-get upgrade
sudo rpi-update


sudo apt-get install build-essential cmake pkg-config

#There are issues installing this packages
#sudo apt-get install libjpeg8-dev libtiff4-dev libjasper-dev libpng12-dev

sudo apt-get install libgtk2.0-dev

sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev

sudo apt-get install libatlas-base-dev gfortran

wget https://bootstrap.pypa.io/get-pip.py
sudo python get-pip.py


sudo pip install virtualenv virtualenvwrapper
sudo rm -rf ~/.cache/pip

export WORKON_HOME=$HOME/.virtualenvs
source /usr/local/bin/virtualenvwrapper.sh
source ~/.profile
mkvirtualenv cv

sudo apt-get install python2.7-dev

pip install numpy

wget -O opencv-2.4.10.zip http://sourceforge.net/projects/opencvlibrary/files/opencv-unix/2.4.10/opencv-2.4.10.zip/download
unzip opencv-2.4.10.zip
cd opencv-2.4.10

mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_NEW_PYTHON_SUPPORT=ON -D INSTALL_C_EXAMPLES=ON -D INSTALL_PYTHON_EXAMPLES=ON  -D BUILD_EXAMPLES=ON ..

#Getting a fatal error, no directory
make

sudo make install
sudo ldconfig

cd ~/.virtualenvs/cv/lib/python2.7/site-packages/
ln -s /usr/local/lib/python2.7/site-packages/cv2.so cv2.so
ln -s /usr/local/lib/python2.7/site-packages/cv.py cv.py

workon cv
python
>>> import cv2
>>> cv2.__version__
'2.4.10'

#########################

source ~/.profile
workon cv
















Check integrity of the camera

Terminal
#First you must enable the camera on the RasberryPi3
sudo raspi-config
#Now take a stillshot saved in the pi\ directory as test.jpg
raspistill -o test.jpg












