# DIY Pixelstick using Teensy

Inspired by [Philippe Dubost light painting](https://www.youtube.com/watch?v=Hau4WGgDPHA), let's build our own Pixelstick using Teensy!

![&quot;It&apos;s Going to Be OK&quot; by Philippe Dubost](https://scontent-arn2-1.xx.fbcdn.net/v/t1.0-9/91521406_10157302808901219_5205234096254484480_o.jpg?_nc_cat=102&_nc_sid=8024bb&_nc_ohc=gEOq93riJa8AX-akxcw&_nc_ht=scontent-arn2-1.xx&oh=108c18efaa81be4a4f96851be67f7009&oe=5EBAB124)

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

### Capture the light!

To see the light painting effect, either follow the TouchDesigner guide linked prior, or install a software like [Lightpaint Live](https://lightpaintlive.com/). 

