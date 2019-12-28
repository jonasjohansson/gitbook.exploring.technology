# Motion

### [ADXL326 Triple-Axis Accelerometer](https://www.adafruit.com/product/1018)

{% tabs %}
{% tab title="Product" %}
An accelerometer can measure how its rotated \(its orientation\), along three different axes. Each axis has its own pin which gives an analog signal between 0 to 5 volts. The Arduino can measure these values with its Analog In ports.

![](../../../../.gitbook/assets/image.png)

{% hint style="info" %}
We have these units from Sparkfun and from Adafruit, both work the same way but look slightly different. 
{% endhint %}

{% hint style="warning" %}
The values might come out a bit noisy, this can be fixed by [smoothing the values](https://www.arduino.cc/en/tutorial/smoothing).
{% endhint %}
{% endtab %}

{% tab title="Schematic" %}
| Sensor | Arduino |
| :--- | :--- |
| Vin / VCC | 5V |
| GND | GND |
| Zout | A0 / A5 |
| Yout | A0 / A5 |
| Xout | A0 / A5 |
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {

}

void loop() {
  int valx = analogRead(0);
  int valy = analogRead(1);
  int valz = analogRead(2);

  Serial.print(valx);
  Serial.print(" ");

  Serial.print(valy);
  Serial.print(" ");

  Serial.print(valz);
  Serial.println(" ");
}
```
{% endtab %}
{% endtabs %}



### 

