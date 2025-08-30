# Circuit Python

[CircuitPython home page](https://circuitpython.org).

Welcome To [CircuitPython Tutorial](https://learn.adafruit.com/welcome-to-circuitpython/overview)

## Install

Follow the [general guide](https://learn.adafruit.com/welcome-to-circuitpython/installing-circuitpython) on Circuit Python.

- Find your board and [download](https://circuitpython.org/downloads)
- Connect your board with a data cable.
- You may need to double click the reset button to bring up the boot loader.
- A new disk should appear.  
- Copy the `.uf2` file to the disk.  This will cause the disk to unmount.  
- In a little while, a new disk will appear 'CIRCUITPYTHON'
- On that disk: 
  - `code.py` is the code that will be run
  - `lib` contains libraries
  - `settings.toml` is used to load [environment variables](https://docs.circuitpython.org/en/latest/docs/environment.html)


## Documentation

CircuitPython [API Reference](https://docs.circuitpython.org/en/latest/docs/index.html)

## Libraries

[Library How to use](https://learn.adafruit.com/welcome-to-circuitpython/circuitpython-libraries)

[Library Collection](https://circuitpython.org/libraries)

[on github](https://github.com/adafruit/Adafruit_CircuitPython_Bundle)

[library documentation](https://docs.circuitpython.org/projects/bundle/en/latest/drivers.html)

### Library Documentation

[Adafruit Libraries](https://docs.circuitpython.org/projects/bundle/en/latest/drivers.html)

### circup

[On GitHub](https://github.com/adafruit/circup)

    uv add circup

    # Install all imported modules
    circup install --auto

    # specific
    circup install adafruit_thermal_printer
    circup uninstall adafruit_thermal_printer

    # update:
    circup update


## VS Code

[How to use](https://learn.adafruit.com/using-the-circuitpython-extension-for-visual-studio-code/use-the-circuitpython-extension-for-vs-code)

[Updates](https://learn.adafruit.com/keep-your-circuitpython-libraries-on-devices-up-to-date-with-circup)


## REPL on Mac OS

    screen <tty> 115200

`help("modules")` to list installed modules


## On Raspberry

Install Blinka

for Bluetooth, use [bleak](https://github.com/hbldh/bleak/tree/develop)

Add user to bluetooth group:

    sudo usermod -aG bluetooth pi

