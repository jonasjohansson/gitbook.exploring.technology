# Running NeoPixels over ArtNET with Arduino/Teensy

### Steps

1. Install [ArtNetViewer](http://www.artnetview.com/).
2. Install a pixels to ArtNet software such as [Resolume](https://resolume.com/).
3. Open Arduino &gt; Tools &gt; Manage Libraries… and install `Artnet`, `ArtnetWifi` and `FastLED`.
4. Connect micro-controller and run File &gt; Examples &gt; ArtnetWiFi and select ArtnetWifiFastLED.
5. Change the `ssid` and `password` and upload.
6. Connect an LED strip to the micro-controller on pins defined in the code.

