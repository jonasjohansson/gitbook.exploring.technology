# Hacking

At some point, vanilla __Bitsy will not be enough, meaning, it's time to hack! Now, most hacks require some level of coding, whilst others are more like tools, let's look at those first!

* Add audio \(use [Beetbox](https://www.beepbox.co/)\): [https://candle.itch.io/bitsy-audio](https://candle.itch.io/bitsy-audio)
* Turn an image into pixels: [https://ruin.itch.io/image-to-bitsy](https://ruin.itch.io/image-to-bitsy)
* Generate custom fonts: [https://seansleblanc.itch.io/fontsy](https://seansleblanc.itch.io/fontsy)
* Automagically create exits: [https://voec.github.io/witchery/](https://voec.github.io/witchery/)
* Get all the colours: [https://janosc.itch.io/rgbitsy](https://janosc.itch.io/rgbitsy)
* Merge game data: [https://seansleblanc.itch.io/bitsy-merge](https://seansleblanc.itch.io/bitsy-merge)

## Existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) \(some mentioned below\) extending Bitsy. These hacks are [inserted into the Bitsy HTML file](https://github.com/seleb/bitsy-hacks#how-to-use). If that process feels too complex, [Borksy](https://ayolland.itch.io/borksy) allows hacks to be easily toggled!

{% hint style="warning" %}
Some hacks are more or less difficult to implement, and in overall getting a hack to work as intended requires dedication and learning!
{% endhint %}

| Hack | Description |
| :--- | :--- |
| [Exit on dialog](https://seleb.github.io/bitsy-hacks/dist/exit-from-dialog.js) | Lets you exit to another room from dialog \(including inside conditionals\). Use it to make an invisible sprite that acts as a conditional exit, use it to warp somewhere after a conversation, use it to put a guard at your gate who only lets you in once you're disguised, use it to require payment before the ferryman will take you across the river. |
| [Dialog prompt](https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-prompt.js) | Adds a dialog command which prompts the user for input, and stores the result in a variable. |
| [Transparent sprites](https://github.com/seleb/bitsy-hacks/blob/master/dist/transparent-sprites.js) | Makes all sprites have transparent backgrounds \(tiles can be seen underneath the player, sprites, and items\). |
| [Solid items](https://github.com/seleb/bitsy-hacks/blob/master/dist/solid-items.js) | Prevents certain items from being picked up or walked over, but still triggers their dialog. This allows them to be treated like sprites that can be placed multiple times. |
| [Music per room and sound effects](https://github.com/seleb/bitsy-hacks/blob/master/dist/bitsymuse.js) | A hack that adds a variety of audio controls, including music that changes as you move between rooms. If the same song is played as you move between rooms, the audio file will continue playing. |

### Adding hack

These are the steps to follow:

1. Find the code to the hack of interest \([example](https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-audio.js)\)
2. Copy & paste the code into the HTML file \(see below\)
3. Follow the code instructions
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

