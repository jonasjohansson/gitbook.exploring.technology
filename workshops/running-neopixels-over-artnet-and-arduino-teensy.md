# Running NeoPixels over ArtNET with Arduino/Teensy

### Steps

1. Install a pixels to ArtNet software such as [Resolume](https://resolume.com/), [Jinx](http://www.live-leds.de/) or [Glediator](https://oneguyoneblog.com/download/glediator-v2-0-3/).
2. Download [Artnet](https://github.com/natcl/Artnet) and [ArtnetWifi](https://github.com/rstephan/ArtnetWifi) libraries
3. In Arduino go to Tools &gt; Manage Libraries… and install `NeoPixel` and `FastLED`
4. In Arduino go to Sketch &gt; Include Library &gt; Add .ZIP Library… and select the ZIP files

For both examples make sure to update `numLeds` to match the length of the LED strip, and to attach the LED strip according to the `dataPin`.

{% hint style="info" %}
For debugging ArtNet install [ArtNetViewer](http://www.artnetview.com/).
{% endhint %}

### ArtNET over Serial

1. Open File &gt; Examples &gt; Artnet &gt; NeoPixel &gt; ArtnetNeoPixel.
2. Update `ip`, `mac` and `broadcast` according to your computer \(use `ifconfig en0` in the Terminal\).

### ArtNET over WIFI

1. Open File &gt; Examples &gt; ArtnetWifi &gt; ArtnetWifiNeoPixel.
2. Update `ssid` and `password` according to your network.

### Related links

* [https://learn.sparkfun.com/tutorials/using-artnet-dmx-and-the-esp32-to-drive-pixels/all](https://learn.sparkfun.com/tutorials/using-artnet-dmx-and-the-esp32-to-drive-pixels/all)

