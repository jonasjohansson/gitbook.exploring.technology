---
description: Written by Alexander Wallin
---

# Creating sound and music with Tone.js

Create, combine and control sounds in the browser using [Tone.js](https://tonejs.github.io/), sprinkle  keyboard and mouse interaction, and bring it together with some tasty [P5](../../learn/p5/) visuals!

While [Web Audio API fundamentals](https://developer.mozilla.org/en/docs/Web/API/Web_Audio_API) is mentioned, the main focus is to get going and playing! As other official APIs, it is quite verbose and can be awkward in the beginning. Hopefully, once you've played with Tone it will be easier to grasp the Web Audio API if you want to dive deeper.

{% hint style="info" %}
Looking for sounds? Use the [Wikimedia Commons Sound](https://commons.wikimedia.org/wiki/Category:Sound) database or [Alexander Wallins sound repository](https://www.alexanderwallin.com/audio/inventory.json).
{% endhint %}

## History of Web Audio

To understand where we are, let's briefly look in the rear-view mirror to where we've been. For a more thorough history lesson, [read this introduction](https://webaudioapi.com/book/Web_Audio_API_Boris_Smus_html/ch01.html) web audio, it's background and development.

#### 1995

FutureSplash \(later Flash\) is released and quickly adopted, dominating interactive websites for a long time to come.

#### 2001

Audio playback in HTML is introduced using the `<bgsound>` tag.

#### 2011

The first draft of the Web Audio API is released

#### 2014

The first version of HTML5 and its `<audio>` tag is released.

#### 2017

The [Audio Worklet](https://developer.mozilla.org/en-US/docs/Web/API/AudioWorklet) feature makes it possible to process audio completely separate from other JavaScript stuff, making it more performant.

