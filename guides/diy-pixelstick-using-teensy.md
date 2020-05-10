---
description: Written by Jonas Johansson and Victoria Albrecht
---

# DIY Pixelstick using Teensy

Inspired by [Philippe Dubost light painting](https://www.youtube.com/watch?v=Hau4WGgDPHA), let's build our own Pixelstick using Teensy!

* [https://www.instagram.com/p/B\_0liw-HoG6/](https://www.instagram.com/p/B_0liw-HoG6/)

### Materials

| Qty | Item |
| :--- | :--- |
| 1 | [Aluminum U Profile](https://www.xcen.se/aluprofil-uprofil-hog-alu) \([alt1](https://www.kjell.com/se/produkter/hem-kontor-fritid/belysning/led-lister/nextec/nextec-aluminiumprofil-utanpaliggande-for-led-lister-p36321), [alt2,](https://www.ebay.com/itm/1-10m-LED-Aluminium-Profil-Abdeckung-Clips-Endkappen-Alu-Schiene/231960996121) [alt3](https://www.led-tejp.se/aluprofil-uprofil-lag)\) |
| 1 | [NeoPixel 144 LED/m](https://www.adafruit.com/product/1506) |
| 1 | [Teensy 3.6](https://www.pjrc.com/store/teensy36.html) \(or add [SD reader](https://www.adafruit.com/product/254) to an Arduino\) |
| 1 | [2-Axis Joystick](https://www.adafruit.com/product/444) \(or 2 [buttons](https://www.adafruit.com/product/1119)\) |
| 1 | [Anker PowerCore](https://www.anker.com/products/variant/powercore-20100/A1271012) \(dual 2.4A battery\) |

## Getting started

### Generate TXT from PNG

Download the [Pixelstick repository](https://github.com/LucasBerbesson/pixelstick) and follow the steps to generate a text file from image. Make sure the image is **RGB** with a **black** \(\#000000\) background and **white** \(\#FFFFFF\) text. Try to avoid varied levels of opacity.

To install the Python Image Library do the following in the Terminal \(only do line 1-2 if Pip is not installed\):

```python
sudo easy_install pip
sudo pip install --upgrade pip
sudo pip install image
```

{% hint style="info" %}
You will be required to enter your password when using the `sudo` command.
{% endhint %}

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

For this project a custom version of the [pixelstick.ino](https://github.com/jonasjohansson/pixelstick) was made can be found here, and comes with some changes:

* The text files are sorted alphabetically \(install the [ArduinoSort](https://github.com/emilv/ArduinoSort) library\)
* The current index is displayed using the LED strip
* Two buttons are used for moving between text files and playing/stopping an animation

### Capture the light!

To see the light painting effect, either follow the TouchDesigner guide linked prior, or install a software like [Lightpaint Live](https://lightpaintlive.com/).

If the lights shine too bright it is possible to set the total brightness of the strip by adding `strip.setBrightness(50);` in `setup` where 50 can be a value between 0-255.

{% hint style="danger" %}
144 pixels in full white will draw ~8.64 Amps, which is way beyond the 2.4A and even 4.8A of the powerbank. Make sure to reduce brightness and consider the width and height of the light pattern.
{% endhint %}

