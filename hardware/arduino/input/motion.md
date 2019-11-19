# Motion

### [ADXL326 Triple-Axis Accelerometer](https://www.adafruit.com/product/1018)

{% tabs %}
{% tab title="Product" %}
An accelerometer can measure how its rotated \(its orientation\), along three different axes. Each axis has its own pin which gives an analog signal between 0 to 5 volts. The Arduino can measure these values with its Analog In ports.

{% hint style="warning" %}
The values might come out a bit noisy, this can be fixed by [smoothing the values](https://www.arduino.cc/en/tutorial/smoothing).
{% endhint %}

![](https://cdn-shop.adafruit.com/970x728/1018-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
| Sensor | Arduino |
| :--- | :--- |
| Vin | 5V |
| GND | GND |
| Zout | A0 / A5 |
| Yout | A0 / A5 |
| Xout | A0 / A5 |
{% endtab %}
{% endtabs %}

### 

