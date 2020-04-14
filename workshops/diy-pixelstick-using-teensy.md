# DIY Pixelstick using Teensy

### Generate TXT from PNG

Download the [Pixelstick repository](https://github.com/LucasBerbesson/pixelstick) and follow the steps to generate a text file from image. 

To install the Python Image Library do the following in the Terminal \(only do line 1-2 if Pip is not installed\):

```python
sudo easy_install pip
sudo pip install --upgrade pip
sudo pip install image
```

### Format SD

1. Download and install [SD Card Formatter](https://www.sdcard.org/downloads/formatter/)
2. Open SD Card Formatter, select the card and format.
3. Add files to SD card
4. Eject SD card and place in Teensy

### Install Teensyduino & Neopixel Library

1. To run Arduino code on Teensy using the Arduino IDE we must install [Teensyduino](https://www.pjrc.com/teensy/td_download.html).
2. With Teensyduino open, go to **Tools** and **Manage Libraries…** type in "Adafruit NeoPixel" and install the option with the same name.

### Upload code to Teensy

Create a new sketch `⌘ + N` and run the `pixelstick.ino` file from the repository, with some minor changes:

1. `SDPin 4` should be `SDpin BUILTIN_SDCARD` 
2. Comment out line 150-154 as no button is used

Since the Teensy provides 3.3 volts the LED strip will not manage to produce full white, but instead go into red. There are ways to avoid this such as using the [OctoWS2811](https://www.pjrc.com/teensy/td_libs_OctoWS2811.html) or simply providing power externally.





