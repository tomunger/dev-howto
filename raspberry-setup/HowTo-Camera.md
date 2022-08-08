# Camera

## Setup

Install the camera module.

Enable the camera using raspberry config, either graphical or:

    sudo raspi-config

Test the camera:  

    raspistill -v -o test.jpg
    raspistill -t 10000000



## OpenCV

[OpenCV](https://opencv.org/)

Install [standard package](https://raspberrypi.stackexchange.com/questions/100253/how-can-i-install-opencv-on-raspberry-pi-4-raspbian-buster)

    apt list python*opencv*
    sudo apt install python3-opencv
    sudo apt install python3-opencv-apps

from this on [using python](https://circuitdigest.com/microcontroller-projects/how-to-install-python-opencv-on-raspberry-pi)

    sudo apt-get install libopencv-dev python-opencv

try:

    import cv2 



## Tutorial

General [discussion of images](https://circuitdigest.com/tutorial/getting-started-with-opencv-image-processing)


## Python

[Using picamera](https://www.pyimagesearch.com/2015/03/30/accessing-the-raspberry-pi-camera-with-opencv-and-python/)




## Facial Recognition

[Tutorial](https://circuitdigest.com/microcontroller-projects/raspberry-pi-and-opencv-based-face-recognition-system)

This codes give me facial recognition.
