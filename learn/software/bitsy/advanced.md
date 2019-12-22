# Advanced

At some point, _regular_ Bitsy will not be enough, meaning, it's time to hack! Now, some hacks require some level of coding, whilst others are straight-forward**.**

## Existing hacks

Thanks to a vibrant community there are [several hacks](https://github.com/seleb/bitsy-hacks) built on Kitsy, a small framework extending Bitsy. These hacks are [inserted into the Bitsy HTML file](https://github.com/seleb/bitsy-hacks#how-to-use), and if that process feels too complex, [Borksy](https://ayolland.itch.io/borksy) allows hacks to be easily toggled!

```markup
  <script>
    // and then paste your code here!
  </script>
</head>
<body onload="startExportedGame()">
  <canvas id="game"></canvas>
</body>
```

### Adding Audio

{% embed url="https://candle.itch.io/bitsy-audio" %}

### Image to Bitsy

{% embed url="https://ruin.itch.io/image-to-bitsy" %}

### Custom fonts

{% embed url="https://seansleblanc.itch.io/fontsy" %}

## Custom hacks

If the hacks available just don't feel right, it's possible to write custom ones [using Kitsy](https://github.com/seleb/bitsy-hacks/wiki). And for a lighter introduction to custom hacking, it's possibly to include a script that listens to Bitsy events, such as `onPlayerMoved()` which happens every time the player avatar moves.

```markup
    <script src="https://gistcdn.githack.com/jonasjohansson/938e71f56ad76c01d9c6f2d7c2fed3c5/raw/e7270bc2bb73315abd7faa6fe50790c7c27ec57d/kitsy-events.js"></script>
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

* \*\*\*\*[**https://if-true-blog.blogspot.com/2019/10/hacking-bitsy-to-run-ai-pt-2-ghosts-n.html**](https://if-true-blog.blogspot.com/2019/10/hacking-bitsy-to-run-ai-pt-2-ghosts-n.html)\*\*\*\*

### **Adding Colors**

It is technically possible to go beyond Bitsy's limited palette by editing the Game Data**.**

