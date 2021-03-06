# Real-time LEDs over Art-Net with Arduino/Teensy and Resolume

Running LEDs on micro-controllers is made easy using the [NeoPixel](https://learn.adafruit.com/adafruit-neopixel-uberguide) or [FastLED](http://fastled.io/) library along with fixtures with WS2812B or SK6812B based LEDs. But what if you want to control the lights using realtime input from a computer? The obvious choice is to use [Art-Net](https://en.wikipedia.org/wiki/Art-Net), a protocol for sending DMX over Ethernet \(and Wifi\), with wide support across software.

## Getting started

This guide assumes that the [Arduino IDE](https://www.arduino.cc/en/Main/Software) is installed along with [Resolume](https://resolume.com/). Use [ArtNetViewer](http://www.artnetview.com/) for debugging. You also need to have either \(or similar alternatives\) of the following:

* Arduino Uno with an [Ethernet shield](https://www.adafruit.com/product/201)
* [Teensy](https://www.pjrc.com/teensy/) using a [Wiz820io](https://www.pjrc.com/store/wiz820_sd_adaptor.html) Ethernet module
* An [Adafruit Feather Huzzah](https://www.adafruit.com/product/2821) \(ESP8226\) and [Arduino MKR1000](https://store.arduino.cc/arduino-mkr1000-wifi) \(WIFI101\)

{% hint style="info" %}
All boards except the Arduino Uno must be explicitly added using the Arduino IDE Board Manager. Some may also require special libraries. Search and you will find.
{% endhint %}

### Preparations

1. Download the [Artnet](https://github.com/natcl/Artnet) and [ArtnetWifi](https://github.com/rstephan/ArtnetWifi) libraries.
2. In Arduino go to Sketch &gt; Include Library &gt; Add .ZIP Library… and select the ZIP files.
3. In Arduino go to Tools &gt; Manage Libraries… then search for \(and install\) `NeoPixel`, `FastLED` and `OctoWS2811` libraries.

{% hint style="info" %}
For the coming examples make sure to update `numLeds` to match the length of the LED strip, and to attach the LED strip according to the `dataPin`.
{% endhint %}

## Ethernet

_For Arduino and Teensy_

1. In Arduino open File &gt; Examples and select Artnet &gt; NeoPixel &gt; ArtnetNeoPixel for Arduino and OctoWS2811 &gt; Artnet for Teensy.
2. Update `ip`, `mac` and `broadcast` \(not required for Teensy\) according to your computer \(use `ifconfig en0` in the Terminal\) and upload.

## Wifi

_For Huzzah and MKR1000_

1. Open File &gt; Examples &gt; ArtnetWifi &gt; ArtnetWifiNeoPixel.
2. Update `ssid` and `password` according to your network and upload.

