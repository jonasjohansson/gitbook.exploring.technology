# 2. Tone.js

We're now going to leave HTML5-land and do things directly in JavaScript. The tool of our choice in this tutorial is [Tone.js](https://tonejs.github.io), a great and vast library for creating sounds and music. Under the hood it uses the Web Audio API, which is the standard API for working with audio in the browser.

To access Tone, include the library with a `<script>` tag. If you are using the P5 editor, open up the sidebar and edit the `index.html` file.

```markup
<script src="https://unpkg.com/tone@13.8.25/build/Tone.js"></script>
```

Great, Tone is live and ready!

### Adding P5

Assuming you are working in the P5 editor or have included P5 some other way, we'll be setting things up inside the `setup()` function. 

The absolute first thing you should always do when working with audio programmatically is to **set a low master volume**. This will save your ears and your happiness. If you play a normalised audio file or make a mistake in your code, you can easily get extremely loud audio in your headphones. 

```javascript
function setup() {
  Tone.Master.volume.value = -24 // decibels
}
```

`Tone.Master` is responsible for routing audio to the main output \(likely your computer speakers or headphones\). Anything that should be audible must connect to it.

### Generating a tone

With the seat belt on we can create our first oscillator using `Tone.Oscillator`. An oscillator generates a sound wave at a certain frequency. It's what makes up most synthezisers!

```javascript
function setup() {
  Tone.Master.volume.value = -24 // decibels
  
  const osc = new Tone.Oscillator({ frequency: 440 })
  osc.start()
}
```

Even though the oscillator is running, we won't be hearing anything. This is because we need to connect it to `Tone.Master` by adding `osc.connect(Tone.Master)`.

Et voilà! You should now hear a tone at 440 Hz \(an A to be precise\). Quite dull and annoying.

{% hint style="info" %}
Press the stop button in the p5 editor to make it stop. We will add better controls for this later.
{% endhint %}

Now that we're generating sound, let's build the Theremin - the world's first synthesizer!

### Related links

* [Tone.Master](https://tonejs.github.io/docs/13.8.25/Master)
* [Tone.Oscillator](https://tonejs.github.io/docs/13.8.25/Gain)

