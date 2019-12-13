# MIDI & OSC

## MIDI

MIDI has been around for a long time but has only recently made its debut in the browser. MIDI \(**M**usical **I**nstrument **D**igital **I**nterface\) is a technical standard that was first published in 1983 and created the means for digital instruments, synthesizers, computers, and various audio devices to communicate with each other. MIDI messages relay musical and time-based information back and forth between devices. To detect MIDI messages transmitted on a computer, use [MIDI Monitor](https://www.snoize.com/MIDIMonitor/)!

MIDI is available directly in the browser through [WebMidi](https://github.com/djipco/webmidi), and comes with [many examples of usage](https://webmidi-examples.glitch.me/).

```markup
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/webmidi"></script>
  </head>
  <body>
    <fieldset>
      <legend>Input</legend>
      <select id="input"></select>
      <button onclick="connectInput()">Connect</button>
    </fieldset>
    <fieldset>
      <legend>Output</legend>
      <select id="output"></select>
      <button onclick="connectOutput()">Connect</button>
    </fieldset>
    <script>
      const inputSelect = document.querySelector("#input");
      const outputSelect = document.querySelector("#output");
      WebMidi.enable(function(err) {
        if (err) {
          console.log("WebMidi could not be enabled.", err);
        }

        for (let input of WebMidi.inputs) {
          var option = document.createElement("option");
          option.textContent = input.name;
          inputSelect.appendChild(option);
        }
        for (let output of WebMidi.outputs) {
          var option = document.createElement("option");
          option.textContent = output.name;
          outputSelect.appendChild(option);
        }
      });

      function connectInput() {
        var input = WebMidi.inputs[inputSelect.selectedIndex];
      }

      function connectOutput() {
        var output = WebMidi.outputs[outputSelect.selectedIndex];
        output.playNote("C3", 1);
      }
    </script>
  </body>
</html>

```

### Hairless MIDI

Combining Arduino with MIDI is a popular route for creating interactive audio objects, and there has been much work enabling the process, with this being one of the best.

1. Install [Hairless MIDI](https://projectgus.github.io/hairless-midiserial/#downloads)
2. Open Audio MIDI Setup
   1. Double-click "IAC Driver"
   2. Toggle "Device is Online"
3. Open Ableton Live
   1. Open Preferences &gt; MIDI
   2. Toggle Track, Sync and Remote for IAC Driver on Input
4. Open Arduino
   1. Open Sketch &gt; Include Library
   2. Change Type to Contributed and Topic to Communication
   3. Search for "MIDI Library" and install the latest version

To include the MIDI library in the Arduino sketch use the following code:

```cpp
#include <MIDI.h>
MIDI_CREATE_DEFAULT_INSTANCE();

void setup() {
  MIDI.begin(MIDI_CHANNEL_OMNI);
  Serial.begin(115200);
}

void loop() {
  MIDI.sendNoteOn(42, 127, 1);
}
```

## OSC

### TouchOSC

