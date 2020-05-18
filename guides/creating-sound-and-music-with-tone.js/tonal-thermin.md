# 🕹 Tonal Theremin

It's difficult playing a mouse controlled Theremin, don't you think? Let's introduce some tonality to make it more pleasant.

Instead of setting the `osc.frequency.value` relative to the mouse cursor, we want to use an array of frequencies. Here are some that sound nice together:

```javascript
const frequencies = [262, 330, 398, 494, 526];
```

Your task is map the mouse `y` position to these frequencies so that a certain mouse position plays a certain frequency. Use the [map\(\)](https://p5js.org/reference/#/p5/map) function or write your own logic.

Feel free to change the frequencies and experiment with the interaction.

### Bonus

Create a **second oscillator** that has a different implementation of how the mouse position is mapped to a frequency.

 For this oscillator, you can multiply the frequency by `2` to go an octave up!

