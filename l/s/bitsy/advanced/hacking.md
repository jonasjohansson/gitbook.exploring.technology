# Hacking

At some point, vanilla __Bitsy will not be enough, meaning, it's time to hack! Now, most hacks require some level of coding, whilst others are more like tools:

* Adding audio: [https://candle.itch.io/bitsy-audio](https://candle.itch.io/bitsy-audio)
* Turn an image into pixels: [https://ruin.itch.io/image-to-bitsy](https://ruin.itch.io/image-to-bitsy)
* Generate custom fonts: [https://seansleblanc.itch.io/fontsy](https://seansleblanc.itch.io/fontsy)
* Automagically create exits connecting rooms: [https://voec.github.io/witchery/](https://voec.github.io/witchery/)

![Witchery connects rooms!](../../../../.gitbook/assets/bitsy-witchery%20%281%29.png)

## Existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) built on Kitsy, a small framework extending Bitsy. These hacks are [inserted into the Bitsy HTML file](https://github.com/seleb/bitsy-hacks#how-to-use), and if that process feels too complex, [Borksy](https://ayolland.itch.io/borksy) allows hacks to be easily toggled!

{% hint style="warning" %}
Some hacks are more or less difficult to implement, and in overall getting a hack to work as intended requires dedication and learning!
{% endhint %}

These are the steps to follow:

1. Find the code to the hack of interest \([example](https://github.com/seleb/bitsy-hacks/blob/master/dist/dialog-audio.js)\)
2. Copy & paste the code into the HTML file \(see below\)
3. Follow the instructions in the code
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

## **Copying Game Data**

It is possible to copy the game data from Bitsy games made by others. Doing so may provide a clear explanation to an effect or design that seem complex. To accomplish this it is imperative to find the game data which rest within the website source code.‌

1. Using Chrome, right click on the game and choose **Inspect**
2. Press ⌘F to open the search window, and type _bitsyGameData_., a _script tag will be highlighted._
3.  Click on the tag and ⌘C to copy it, then paste ⌘V to into the Bitsy Game Data window. Remove the `<script>` tag at the top and bottom.

