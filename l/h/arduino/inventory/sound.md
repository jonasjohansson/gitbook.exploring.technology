# Output

### [Electret Microphone Amplifier](https://learn.adafruit.com/adafruit-agc-electret-microphone-amplifier-max9814)

{% tabs %}
{% tab title="Product" %}
With the Microphone amplifier you can take the microphone signal and feed it into a regular audio jack, or read the volume with the Arduino. 

* [https://learn.adafruit.com/adafruit-microphone-amplifier-breakout/measuring-sound-levels](https://learn.adafruit.com/adafruit-microphone-amplifier-breakout/measuring-sound-levels)

{% hint style="danger" %}
Make all gain adjustments gently. If you feel resistance, stop. The tiny trim pot is delicate and it is easy to damage by turning past the stop.
{% endhint %}

![](https://cdn-shop.adafruit.com/970x728/1713-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
| Sensor pin | Arduino pin |
| :--- | :--- |
| OUT | A0 |
| GND | GND |
| VCC | 5V |
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  double volts = getVolume(50);
  Serial.println(volts);
}

double getVolume(int sampleWindow) {
  unsigned long startMillis = millis();
  unsigned int peakToPeak = 0;
  unsigned int signalMax = 0;
  unsigned int signalMin = 1024;

  while (millis() - startMillis < sampleWindow) {
    unsigned int sample = analogRead(0);
    if (sample < 1024) {
      if (sample > signalMax) {
        signalMax = sample;
      } else if (sample < signalMin) {
        signalMin = sample;
      }
    }
  }

  peakToPeak = signalMax - signalMin;
  double volts = (peakToPeak * 5.0) / 1024;
  return volts;
}
```
{% endtab %}
{% endtabs %}

## Motors



