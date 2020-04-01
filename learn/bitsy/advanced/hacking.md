# Hacking

At some point, vanilla __Bitsy will not be enough, meaning, it's time to hack! Now, most hacks require some level of coding, whilst others are more like tools, let's look at those first!

* Add audio \(use [Beepbox](https://www.beepbox.co/)\): [https://candle.itch.io/bitsy-audio](https://candle.itch.io/bitsy-audio)
* Turn an image into pixels: [https://ruin.itch.io/image-to-bitsy](https://ruin.itch.io/image-to-bitsy)
* Turn an image into a room: [https://hideous-cave-goblin.itch.io/room](https://hideous-cave-goblin.itch.io/room)
* Generate custom fonts: [https://seansleblanc.itch.io/fontsy](https://seansleblanc.itch.io/fontsy)
* Automagically create exits: [https://voec.github.io/witchery/](https://voec.github.io/witchery/)
* Get all the colours: [https://janosc.itch.io/rgbitsy](https://janosc.itch.io/rgbitsy)
* Merge game data: [https://seansleblanc.itch.io/bitsy-merge](https://seansleblanc.itch.io/bitsy-merge)

## Add existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) extending Bitsy. Adding these hacks is non-trivial in most cases, but can prove a difficult at first. Here's two ways of adding them.

### 1. [Borksy](https://ayolland.itch.io/borksy)

Add the game data, toggle the hacks, change the variables and download the tweaked HTML. Thank you Borksy!

{% hint style="success" %}
Borksy also adds useful CSS found here: [https://jonasjohansson.glitch.me/bitsy.css](https://jonasjohansson.glitch.me/bitsy.css)
{% endhint %}

### 2. [Copy & Paste](https://github.com/seleb/bitsy-hacks#how-to-use)

1. Find the code to the hack of interest \([example](https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-audio.js)\)
2. Click **Raw** and copy & paste the code into the HTML file \(see below\)
3. Follow the code instructions at the top of the script
4. Reload the game

If lost, read the original explanation.

```markup
  <script>
    // and then paste your code here!
  </script>
</head>
<body onload="startExportedGame()">
  <canvas id="game"></canvas>
</body>
```

An alternative way of accomplishing same thing with much less code:

1. Copy the raw link URL to the script
2. Visit [https://raw.githack.com/](https://raw.githack.com/) and paste it in the top
3. Copy new the link generated under "Use this URL for development"
4. Add this link in a `<script>` tag under the `src` attribute
5. Overwrite `hackOptions` by writing `window.name_of_script.hackOptions`

### Useful hacks

#### Items

{% tabs %}
{% tab title="Transparent items" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/transparent-sprites.js">
window.transparent_sprites.hackOptions = {
  isTransparent: function(drawing) {
    // return drawing.name == 'cat'; // specific transparent drawing
    // return ['tea', 'flower', 'hat'].indexOf(drawing.name) !== -1; // specific transparent drawing list
    // return drawing.name && drawing.name.indexOf('TRANSPARENT') !== -1; // transparent drawing flag in name
    return true; // all drawings are transparent
  }
};
</script>
```
{% endtab %}

{% tab title="Permanent items" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/permanent-items.js">
window.permanent_items.itemIsPermanent = item => {
  // return item.name && item.name == 'tea'; // specific permanent item
  // return ['tea', 'flower', 'hat'].indexOf(item.name) !== -1; // specific permanent item list
  // return item.name && item.name.indexOf('PERMANENT') !== -1; // permanent item flag in name
  return true; // make all items permanent
};
</script>
```
{% endtab %}

{% tab title="Unique items" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/unique-items.js">
window.unique_items.hackOptions = item => {
  // return item.name && item.name == "tea"; // specific unique item
  // return ['tea', 'flower', 'hat'].indexOf(item.name) !== -1; // specific unique item list
  // return item.name && item.name.indexOf('UNIQUE') !== -1; // unique item flag in name
  return true; // all items are unique
};
</script>
```
{% endtab %}
{% endtabs %}

#### Dialog

{% tabs %}
{% tab title="Transparent dialog" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/transparent-dialog.js"></script>
```
{% endtab %}

{% tab title="Exit from dialog" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/exit-from-dialog.js"></script>
```
{% endtab %}

{% tab title="Dialog audio" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/dialog-audio-vocal-synth.js">
window.dialog_audio_vocal_synth.hackOptions$1 = {
  autoReset: true, // if true, automatically resets the voice to default when dialog is exited
  // list of voices that can be used with the provided dialog command
  // the values use for voice parameters are [base, range] pairs for RNG;
  // e.g. [0.5, 0.1] will produce values between 0.4 and 0.6
  voices: {
    default: {
      // volume randomly applied to each letter
      volume: [0.3, 0.1],
      // pitch randomly applied to each letter
      pitch: [240, 200],
      // vibrato randomly applied to each letter
      vibrato: [0.01, 0.005],
      // how much phonemes to affect tract shape
      phoneme: [0.9, 0.1],
      // multiplier for nasalness (based on phoneme)
      nasal: [0.9, 0.1],
      // multiplier for voiced (based on phoneme)
      voiced: [0.4, 0.2],
      // note: tongue is a modification *on top* of the phoneme modification
      // where to modify
      tonguePosition: [0.5, 0.5],
      // range from the position in which points are modified
      tongueSize: [0.3, 0.2],
      // how much modification is applied (this is a multiplier, so base: 1, range: 0 means no modification)
      tongueAmount: [1.0, 0.1]
    },
    // an example voice which overrides the default's pitch and vibrato
    overrideExample: {
      pitch: [650, 325],
      vibrato: [0.3, 0.1]
    }
  }
};
</script>´
```
{% endtab %}

{% tab title="Edit image from dialog" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/edit-image-from-dialog.js"></script>
```
{% endtab %}

{% tab title="Dialog choices" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/dialog-choices.js"></script>
```
{% endtab %}
{% endtabs %}

#### Avatar

{% tabs %}
{% tab title="Directional avatar" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/directional-avatar.js">
window.directional_avatar.hackOptions = {
  // If `horizontalFlipAllowed` is true:
  // pressing left will make the player's sprite face backwards
  // pressing right will make the player's sprite face forwards
  horizontalFlipAllowed: true,
  // If `verticalFlipAllowed` is true:
  // pressing down will make the player's sprite upside-down
  // pressing up will make the player's sprite right-side up
  verticalFlipAllowed: false
};
</script>
```
{% endtab %}

{% tab title="Character portraits" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/character-portraits.js">
window.character_portraits.hackOptions = {
};
</script>
```
{% endtab %}
{% endtabs %}

#### Other

{% tabs %}
{% tab title="Music per room" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/bitsymuse.js">
window.bitsyMuse.hackOptions = {
  // Put entries in this list for each audio file you want to use
  // the key will be the id needed to play it in dialog tags and the musicByRoom options below,
  // and the value will be the properties of the corresponding <audio> tag (e.g. src, loop, volume)
  // Note: you can add <audio> tags to the html manually if you prefer
  audio: {
    // Note: the entries below are examples that should be removed and replaced with your own audio files
    disco: { src: "./disco.mp3", loop: true, volume: 1 },
    rock: { src: "./rock.mp3", loop: true, volume: 1 },
    metal: { src: "./metal.mp3", loop: true, volume: 1 },
    silence: { src: "./metal.mp3", volume: 0 } // trigger this for silence
  },
  // Put entries in this list for every room ID or name that will change the music
  // If the player moves between rooms with the same audio ID, the music keeps playing seamlessly.
  // Undefined rooms will keep playing whatever music they were last playing
  musicByRoom: {
    1: "disco",
    2: "rock",
    3: "metal",
    4: "S"
  },
  silenceId: "S", // Use this song ID to make a room fall silent.
  resume: false // If true, songs will pause/resume on change; otherwise, they'll stop/play (doesn't affect sound effects)
};
</script>
```
{% endtab %}

{% tab title="Corrupt" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/corrupt.js">
window.corrupt.hackOptions = {
  tilemapFreq: 1,
  tilePixelsFreq: 1,
  spritePixelsFreq: 1,
  itemPixelsFreq: 1,
  fontPixelsFreq: 1,
  paletteFreq: 1,
  globalFreq: 1, // multiplier for all the other `Freq` options
  paletteAmplitude: 10 // how much to corrupt palette by (0-128)
};
</script>
```
{% endtab %}

{% tab title="Gravity" %}
```markup
<script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/gravity.js">
window.gravity.hackOptions = {
};
</script>
```
{% endtab %}
{% endtabs %}

## Create custom hacks

If the hacks available just don't feel right, [write custom ones](https://github.com/seleb/bitsy-hacks/wiki)! And if that feels like a bit too large of a mountain to climb, it's also possibly to include a script that listens to Bitsy events, such as `onPlayerMoved()` which happens every time the player avatar moves.

```markup
    <script src="https://jonasjohansson.glitch.me/kitsy-events.js"></script>
    <script>
      foo.after("onPlayerMoved", function() {
        console.log("onPlayerMoved");
      });
    </script>
  </head>
  <body onload="startExportedGame()">
    <canvas id="game"></canvas>
  </body>
</html>
```

## Useful snippets

{% tabs %}
{% tab title="End game" %}
```javascript
startNarrating( ending[1], true);
```
{% endtab %}
{% endtabs %}

