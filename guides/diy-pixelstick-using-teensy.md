---
description: By Jonas Johansson and Victoria Albrecht
---

# DIY Pixelstick using Teensy

Inspired by [Philippe Dubost light painting](https://www.youtube.com/watch?v=Hau4WGgDPHA), let's build our own Pixelstick using Teensy!

### BOM

* [https://www.xcen.se/aluprofil-uprofil-hog-alu](https://www.xcen.se/aluprofil-uprofil-hog-alu)
* [https://www.ebay.com/itm/1-10m-LED-Aluminium-Profil-Abdeckung-Clips-Endkappen-Alu-Schiene/231960996121](https://www.ebay.com/itm/1-10m-LED-Aluminium-Profil-Abdeckung-Clips-Endkappen-Alu-Schiene/231960996121)
* [https://www.led-tejp.se/aluprofil-uprofil-lag](https://www.led-tejp.se/aluprofil-uprofil-lag)
* [https://www.adafruit.com/product/2437](https://www.adafruit.com/product/2437)
* [https://www.adafruit.com/product/2434](https://www.adafruit.com/product/2434)
* [https://www.kjell.com/se/produkter/hem-kontor-fritid/belysning/led-lister/nextec/nextec-aluminiumprofil-utanpaliggande-for-led-lister-p36321](https://www.kjell.com/se/produkter/hem-kontor-fritid/belysning/led-lister/nextec/nextec-aluminiumprofil-utanpaliggande-for-led-lister-p36321)

### Generate TXT from PNG

Download the [Pixelstick repository](https://github.com/LucasBerbesson/pixelstick) and follow the steps to generate a text file from image. Make sure the image is **RGB** with a **black** \(\#000000\) background and **white** \(\#FFFFFF\) text. Try to avoid varied levels of opacity. 

Use simple colors such as red, green and blue as these colors will use less power than white.

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

### Capture the light!

To see the light painting effect, either follow the TouchDesigner guide linked prior, or install a software like [Lightpaint Live](https://lightpaintlive.com/).

If the lights shine too bright it is possible to set the total brightness of the strip by adding `strip.setBrightness(50);` in `setup` where 50 can be a value between 0-255.

