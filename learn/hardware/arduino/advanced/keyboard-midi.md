# Keyboard

The Arduino Uno is not recognised as a HID \(keyboard, mouse\) which disables the functionality of being able to trigger keyboard presses or mouse movements. To use the Arduino Uno as a keyboard there are two options; running [Mio](../../../../tools/mio.md), a custom software listening to the serial communication, and flashing the controller with keyboard enabled firmware.

An alternative to the Arduino Uno is the [Arduino Leonardo](https://www.arduino.cc/en/Main/Arduino_BoardLeonardo) and [Makey Makey](../../makey-makey/), which works natively as a keyboard and mouse.

### Flashing firmware

1. [https://www.arduino.cc/en/Hacking/DFUProgramming8U2](https://www.arduino.cc/en/Hacking/DFUProgramming8U2)
2. [https://github.com/BlitzCityDIY/arduinoMacroKeyboard](https://github.com/BlitzCityDIY/arduinoMacroKeyboard)

`sudo dfu-programmer atmega16u2 erase  
sudo dfu-programmer atmega16u2 flash --debug 1 Arduino-keyboard-0.3.hex  
sudo dfu-programmer atmega16u2 reset`

`sudo dfu-programmer atmega16u2 erase  
sudo dfu-programmer atmega16u2 flash --debug 1 Arduino-usbserial-uno.hex  
sudo dfu-programmer atmega16u2 reset`

