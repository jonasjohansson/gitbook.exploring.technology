# Keyboard

The Arduino Uno is not recognised as a HID \(keyboard, mouse\) which disables the functionality of being able to trigger keyboard presses or mouse movements. To use the Arduino Uno as a keyboard there are two options; running a custom software listening to the serial communication, and flashing the controller with keyboard enabled firmware.

### Serial to keypress

1. Install [Node.js 11.15.0](https://nodejs.org/download/release/v11.15.0/) \([Mac](https://nodejs.org/download/release/v11.15.0/node-v11.15.0.pkg)\)
2. Download and unzip [this package](https://github.com/jonasjohansson/anyino).
3. Open Terminal \(⌘+Space and type Terminal\) and type `cd` followed by a space. Then, drag and drop the "serial-keyboard" onto the terminal window and press Enter.
   1. Type `sudo xcode-select --install` and press Enter \(you will be asked for your password\)
   2. When installed, type `sudo npm install` and press Enter
   3. Type `node main.js`
4. Run the following Arduino code:

```cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
  // trigger a key
  // type $ followed by the name of the key
  Serial.println("$up"); // this triggers the up-key
  delay(500);
  // in order to trigger it again, it must be "un-triggered"
  // type ! followed by the name of the key
  Serial.println("!up");
  delay(500);
}
```

{% hint style="danger" %}
It's not possible to have the Serial Monitor running at the same time as the script. Either close the monitor, or close the script. The script can be closed by focusing the terminal window and pressing Ctrl+C.
{% endhint %}

To map keys to MIDI within Ableton Live use [this guide](https://docs.google.com/presentation/d/1xjRhla6aTVtzeQlrOa1kbYAJJDvl3UsJot2TUJzc7BY/edit#slide=id.g707c928d06_0_63) by Francesco Torelli.

{% page-ref page="../../makey-makey/output.md" %}

### Keyboard firmware

1. [https://www.arduino.cc/en/Hacking/DFUProgramming8U2](https://www.arduino.cc/en/Hacking/DFUProgramming8U2)
2. [https://github.com/BlitzCityDIY/arduinoMacroKeyboard](https://github.com/BlitzCityDIY/arduinoMacroKeyboard)

`sudo dfu-programmer atmega16u2 erase  
sudo dfu-programmer atmega16u2 flash --debug 1 Arduino-keyboard-0.3.hex  
sudo dfu-programmer atmega16u2 reset`

`sudo dfu-programmer atmega16u2 erase  
sudo dfu-programmer atmega16u2 flash --debug 1 Arduino-usbserial-uno.hex  
sudo dfu-programmer atmega16u2 reset`

