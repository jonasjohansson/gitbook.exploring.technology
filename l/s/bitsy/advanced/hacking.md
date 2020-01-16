# Hacking

At some point, vanilla __Bitsy will not be enough, meaning, it's time to hack! Now, most hacks require some level of coding, whilst others are more like tools, let's look at those first!

* Add audio \(use [Beetbox](https://www.beepbox.co/)\): [https://candle.itch.io/bitsy-audio](https://candle.itch.io/bitsy-audio)
* Turn an image into pixels: [https://ruin.itch.io/image-to-bitsy](https://ruin.itch.io/image-to-bitsy)
* Generate custom fonts: [https://seansleblanc.itch.io/fontsy](https://seansleblanc.itch.io/fontsy)
* Automagically create exits: [https://voec.github.io/witchery/](https://voec.github.io/witchery/)
* Get all the colours: [https://janosc.itch.io/rgbitsy](https://janosc.itch.io/rgbitsy)
* Merge game data: [https://seansleblanc.itch.io/bitsy-merge](https://seansleblanc.itch.io/bitsy-merge)

## Existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) extending Bitsy. These hacks are [inserted into the Bitsy HTML file](https://github.com/seleb/bitsy-hacks#how-to-use). If that process feels too complex, [Borksy](https://ayolland.itch.io/borksy) allows hacks to be easily toggled!

### Adding the hack

1. Find the code to the hack of interest \([example](https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-audio.js)\)
2. Click **Raw** and copy & paste the code into the HTML file \(see below\)
3. Follow the code instructions at the top of the script
4. Reload the game

```markup
  <script>
    // and then paste your code here!
  </script>
</head>
<body onload="startExportedGame()">
  <canvas id="game"></canvas>
</body>
```

An alternative way of accomplishing the same thing with much less code:

1. Copy the raw link URL to the script
2. Visit [https://raw.githack.com/](https://raw.githack.com/) and paste it in the top
3. Copy new the link generated under "Use this URL for development"
4. Add this link in a `<script>` tag under the `src` attribute
5. Overwrite `hackOptions` by writing `window.nameOfScrip.hackOptions`

An example including some hacks.

```markup
<head>
  <script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/exit-from-dialog.js"></script>

  <script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/transparent-sprites.js">
    window.transparent_sprites.hackOptions = {
    isTransparent: function (drawing) {
    // return drawing.name == 'tea'; // specific transparent drawing
    // return ['tea', 'flower', 'hat'].indexOf(drawing.name) !== -1; // specific transparent drawing list
    // return drawing.name && drawing.name.indexOf('TRANSPARENT') !== -1; // transparent drawing flag in name
    return true; // all drawings are transparent
    },
    };
  </script>

  <script src="https://raw.githack.com/seleb/bitsy-hacks/master/dist/bitsymuse.js">
    window.bitsyMuse.hackOptions = {
    // Put entries in this list for each audio file you want to use
    // the key will be the id needed to play it in dialog tags and the musicByRoom options below,
    // and the value will be the properties of the corresponding <audio> tag (e.g. src, loop, volume)
    // Note: you can add <audio> tags to the html manually if you prefer
    audio: {
    // Note: the entries below are examples that should be removed and replaced with your own audio files
    'disco': { src: './disco.mp3', loop: true, volume: 1 },
    'rock': { src: './rock.mp3', loop: true, volume: 1  },
    'metal': { src: './metal.mp3', loop: true, volume: 1 },
    },
    // Put entries in this list for every room ID or name that will change the music
    // If the player moves between rooms with the same audio ID, the music keeps playing seamlessly.
    // Undefined rooms will keep playing whatever music they were last playing
    musicByRoom: {
    1: 'disco',
    2: 'rock',
    3: 'metal',
    4: 'S'
    },
    silenceId: 'S', // Use this song ID to make a room fall silent.
    resume: false, // If true, songs will pause/resume on change; otherwise, they'll stop/play (doesn't affect sound effects)
    };
  </script>
</head>

<body onload="startExportedGame()">
  <canvas id="game"></canvas>
</body>
```

## Custom hacks

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

