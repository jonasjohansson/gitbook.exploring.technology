# Hacking

At some point, vanilla __Bitsy will not be enough, meaning, it's time to hack! Now, most hacks require some level of coding, whilst others are more like tools, let's look at those!

## Tools

* Turn an image into pixels: [https://ruin.itch.io/image-to-bitsy](https://ruin.itch.io/image-to-bitsy)
* Generate custom fonts: [https://seansleblanc.itch.io/fontsy](https://seansleblanc.itch.io/fontsy)
* Automagically create exits: [https://voec.github.io/witchery/](https://voec.github.io/witchery/)
* Get all the colours: [https://janosc.itch.io/rgbitsy](https://janosc.itch.io/rgbitsy)
* Merge game data: [https://seansleblanc.itch.io/bitsy-merge](https://seansleblanc.itch.io/bitsy-merge)

![](../../../../.gitbook/assets/bitsy-witchery%20%281%29.png)

### Adding audio

It's dead simple adding audio! 

1. Dowload your Bitsy project as HTML
2. Create a sound file using [Beepbox](https://www.beepbox.co/#8n31s0k0l00e03t2mm0a7g0fj07i0r1o3210T1v1L4u56q1d1f8y3z7C1c0A5F5B9V7Q0001PfaedE0067T1v1L4uebq3d5f8y6z8C0c2A9F6B9V1Q0681Pd756E00c2T1v1L4u37q1d1f6y1z6C1c0AbF6B0V1Q07beP9996E0006T2v1L4u15q0d1f8y0z1C2w0b4h400000000h4g000000014h000000004h400000000p16000000), [Ableton](https://www.ableton.com/) or with a sound file found from somewhere
3. Visit [https://candle.itch.io/bitsy-audio](https://candle.itch.io/bitsy-audio) and follow the instructions!

## Existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) \(some mentioned below\) extending Bitsy. These hacks are [inserted into the Bitsy HTML file](https://github.com/seleb/bitsy-hacks#how-to-use). If that process feels too complex, [Borksy](https://ayolland.itch.io/borksy) allows hacks to be easily toggled!

{% hint style="warning" %}
Some hacks are more or less difficult to implement, and in overall getting a hack to work as intended requires dedication and learning!
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Hack</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><a href="https://seleb.github.io/bitsy-hacks/dist/exit-from-dialog.js">Exit on dialog</a>
      </td>
      <td style="text-align:left">Lets you exit to another room from dialog (including inside conditionals).
        Use it to make an invisible sprite that acts as a conditional exit, use
        it to warp somewhere after a conversation, use it to put a guard at your
        gate who only lets you in once you&apos;re disguised, use it to require
        payment before the ferryman will take you across the river.</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-prompt.js">Dialog prompt</a>
      </td>
      <td style="text-align:left">
        <p>Adds a dialog command which prompts the user for input,</p>
        <p>and stores the result in a variable.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://github.com/seleb/bitsy-hacks/blob/master/dist/transparent-sprites.js">Transparent sprites</a>
      </td>
      <td style="text-align:left">Makes all sprites have transparent backgrounds (tiles can be seen underneath
        the player, sprites, and items).</td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://github.com/seleb/bitsy-hacks/blob/master/dist/solid-items.js">Solid items</a>
      </td>
      <td style="text-align:left">Prevents certain items from being picked up or walked over, but still
        triggers their dialog. This allows them to be treated like sprites that
        can be placed multiple times.</td>
    </tr>
  </tbody>
</table>### Adding hack

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

