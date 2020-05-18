# 🕹 Task: Make the Theremin tonal

It's pretty difficult playing a mouse controlled Theremin, don't you think? Let's introduce some tonality to make it more pleasant.

Here are a set of frequencies that sound pretty nice together:

```javascript
const frequencies = [262, 330, 398, 494, 526]
```

Your task is to somehow map the mouse's `y` position to these frequencies so that a certain mouse position plays a certain frequency. You can make it go up and down the notes as you drag the mouse up and down the window, or you can come up with something else, it's up to you.

{% hint style="info" %}
Bonus task: Create a second oscillator that has a different implementation of how the mouse position is mapped to a frequency. For this oscillator, you can multiply the frequency by `2` to go an octave up!
{% endhint %}

