# Midi

Combining Arduino with MIDI is a popular route for creating interactive audio objects, and there has been much work enabling the process, let's try it!

### Hairless MIDI

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

