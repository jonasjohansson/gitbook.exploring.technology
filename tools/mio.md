# Mio

Mio simplifies serial communication as a trigger for key presses and MIDI communication. It relies on specific commands and values being sent from a device over a serial line. The command and value will then be parsed, leaving only the value.

{% hint style="warning" %}
Because Mio is made by an Unidentified Developer \(me, Jonas\) the Control key must be pressed while clicking the app icon. Then choose **Open** from the menu.
{% endhint %}

All key logic is handled on  the device and sent to Mio via serial. The message should be written with a **$ dollar** sign followed by the key to press eg. **$down**.

{% tabs %}
{% tab title=" Code" %}
```csharp
void setup() {
  Serial.begin(9600);
  pinMode(2, INPUT_PULLUP);
  pinMode(3, INPUT_PULLUP);
  pinMode(4, INPUT_PULLUP);
  pinMode(5, INPUT_PULLUP);
}

void loop() { 
  int btn1 = digitalRead(2);
  int btn2 = digitalRead(3);
  int btn3 = digitalRead(4);
  int btn4 = digitalRead(5);
  
  if (btn1 == LOW){
    Serial.println("$up");
  }
  
  if (btn2 == LOW){
    Serial.println("$down");
  }
  
  if (btn3 == LOW){
    Serial.println("$left");
  }
  
  if (btn4 == LOW){
    Serial.println("$right");
  }
}
```
{% endtab %}

{% tab title="Schematic" %}
| Button Pin  | Arduino Pin |
| :--- | :--- |
| Button 1 \(orange wire\) | Digital 0 |
| Button 2 \(green wire\) | Digital 1 |
| Button 3 \(blue wire\) | Digital 2 |
| Button 4 \(purple wire\) | Digital 3 |

![](../.gitbook/assets/image%20%287%29.png)
{% endtab %}
{% endtabs %}

### Permission

In order to control the keyboard Mio requires permissions. On Mac go to System preferences &gt; Security & Privacy, unlock the page by clicking the lock and providing the password, and then under Accessibility find Mio and tick the box. 

{% hint style="danger" %}
If a new version has been installed, this might have to be done again by toggling the Mio checkbox!
{% endhint %}

![](../.gitbook/assets/permissions.png)

## 

