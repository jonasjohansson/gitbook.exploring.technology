# 4. Playing Audio Files

We have taken a first look at generating \(or synthesizing\) sound, and now it's time to master audio file playback. Use `Tone.Player` to load a sound.

```javascript
let player

function setup() {
  Tone.Master.volume.value = -24
  
  player = new Tone.Player({
    url: 'https://www.alexanderwallin.com/audio/pad-4.ogg',
    onload: function() {
      player.start()
    }
  })
  player.connect(Tone.Master)
}
```

That's should play a short but cute synth sample. We can `restart()` it whenever we want, perhaps inside `mouseClicked()`?

```javascript
function mouseClicked() {
  player.restart()
}
```

Click the canvas and Bob will be your uncle! We can also make it loop, fade in and out and even play in reverse!

### Related links

* [Tone.Player](https://tonejs.github.io/docs/13.8.25/Player)
* [Tone.Sampler](https://tonejs.github.io/docs/13.8.25/Sampler)

