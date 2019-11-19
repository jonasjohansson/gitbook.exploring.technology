# Sound

### [Electret Microphone Amplifier](https://learn.adafruit.com/adafruit-agc-electret-microphone-amplifier-max9814)

{% tabs %}
{% tab title="Product" %}
With the Microphone amplifier you can take the microphone signal and feed it into a regular audiojack, or read the volume with the Arduino. 

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
/****************************************
Example Sound Level Sketch for the 
Adafruit Microphone Amplifier
****************************************/

const int sampleWindow = 50; // Sample window width in mS (50 mS = 20Hz)
unsigned int sample;

void setup() 
{
   Serial.begin(9600);
}


void loop() 
{
   double volts = getVolume();
   Serial.println(volts);
}

double getVolume() {
   unsigned long startMillis= millis();  // Start of sample window
      unsigned int peakToPeak = 0;   // peak-to-peak level
   
      unsigned int signalMax = 0;
      unsigned int signalMin = 1024;
   
      // collect data for 50 mS
      while (millis() - startMillis < sampleWindow)
      {
         sample = analogRead(0);
         if (sample < 1024)  // toss out spurious readings
         {
            if (sample > signalMax)
            {
               signalMax = sample;  // save just the max levels
            }
            else if (sample < signalMin)
            {
               signalMin = sample;  // save just the min levels
            }
         }
      }
      peakToPeak = signalMax - signalMin;  // max - min = peak-peak amplitude
      double volts = (peakToPeak * 5.0) / 1024;  // convert to volts
      return volts;
   }
```
{% endtab %}
{% endtabs %}

### References

* [https://learn.adafruit.com/adafruit-microphone-amplifier-breakout/measuring-sound-levels](https://learn.adafruit.com/adafruit-microphone-amplifier-breakout/measuring-sound-levels)



