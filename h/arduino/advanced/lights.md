# Lights

1. Install the NeoPixel Library

### Neopixels

```csharp
#include <Adafruit_NeoPixel.h>

int neoPin = 6;
int numPixels = 4;

Adafruit_NeoPixel pixels = Adafruit_NeoPixel(numPixels, neoPin, NEO_GRB + NEO_KHZ800);

void setup() {
  pixels.begin();
  pixels.show(); // turns neopixels black at start
}

void loop(){
  pixels.setPixelColor(0, pixels.Color(255,0,0));
  pixels.setPixelColor(1, pixels.Color(0,255,0));
  pixels.setPixelColor(2, pixels.Color(0,0,255));
  pixels.setPixelColor(3, pixels.Color(255,255,255));
  pixels.show();
}
```

### Neopixels + For loop

```csharp
#include <Adafruit_NeoPixel.h>

int neoPin = 6;
int numPixels = 4;
int delayTime = 200;

Adafruit_NeoPixel pixels = Adafruit_NeoPixel(numPixels, neoPin, NEO_GRB + NEO_KHZ800);

void setup() {
  pixels.begin();
  pixels.show(); // turns neopixels black at start
}

void loop(){
  for (int i = 0; i < numPixels; i++){
    pixels.setPixelColor(i, pixels.Color(255,255,255));
    delay(delayTime);
    pixels.show();
  }
}
```

