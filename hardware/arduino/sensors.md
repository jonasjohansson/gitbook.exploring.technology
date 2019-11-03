# Sensors

### [IR Proximity](https://www.adafruit.com/product/164)

{% tabs %}
{% tab title="Image" %}
![](https://cdn-shop.adafruit.com/970x728/164-00.jpg)
{% endtab %}

{% tab title="Schematic" %}
![](../../.gitbook/assets/ir-proximity.png)
{% endtab %}

{% tab title="Code" %}
```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  int val = analogRead(A3);
  // convert sensor reading into 0-255
  // change 0-600 to whatever fits your sensor
  int mappedVal = map(val,0,600,0,255);
  Serial.print(val);
  Serial.print("\t");
  Serial.println(val);
}
```
{% endtab %}
{% endtabs %}

### [Maxbotix Ultrasonic Rangefinder](https://www.adafruit.com/product/172)

{% tabs %}
{% tab title="Image" %}
![](https://cdn-shop.adafruit.com/970x728/172-00.jpg)
{% endtab %}
{% endtabs %}

### [Force Sensitive Resistor \(FSR\)](https://www.adafruit.com/product/1075)

{% tabs %}
{% tab title="Image" %}
![](https://cdn-shop.adafruit.com/970x728/1075-01.jpg)
{% endtab %}
{% endtabs %}



