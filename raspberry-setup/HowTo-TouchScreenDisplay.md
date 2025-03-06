# Raspbery Pi TouchScreen

[Documentation](https://www.raspberrypi.com/documentation/accessories/display.html)

[Troubleshooting](https://www.raspberrypi.com/documentation/accessories/display.html#troubleshooting-the-display)

Confirm the screen has been detected:

    dmesg | grep -i ft5406

## Orientation / Rotation

The screen can be rotated in the desktop with screen configuration.

However, [rotating the screen with out a desktop](https://www.raspberrypi.com/documentation/accessories/display.html#rotate-screen-without-a-desktop)
is problematic.  There are a couple wys to do this, but they rotate only the display, not touch input.  
That has to be rotated in a separate step.  

I've concluded it is easier to rotate the hardware.
