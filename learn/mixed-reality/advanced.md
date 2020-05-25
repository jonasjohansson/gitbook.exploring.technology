# 8. Custom Components

A-Frame has a huge community developing special _components_ that can does very advanced things with minimal amounts of code. For all of these it's not only to copy and paste but you are expected to read their documentation in order to fully understand how to use it. Most of the time there's a lot of custom attributes that come along.

## Particles

Ever heard the concept of particles in CGI? It's an amazing thing that allows us to create the illusion of rain, snow, fire, dust and much more. In A-Frame you can easily get started by including the [A-Frame Particle System](https://www.npmjs.com/package/aframe-particle-system-component) script!

```markup
<script src="https://unpkg.com/aframe-particle-system-component@1.0.x/dist/aframe-particle-system-component.min.js"></script> 
```

And then add the attribute _particle-system_ along with some parameters and off you go!

```markup
<a-entity particle-system="color: #EF0000,#44CC00"></a-entity>
```

## Voice Recognition

{% hint style="danger" %}
Does not work on mobile!
{% endhint %}

Do you want to control your visuals through voice? That's a rhetorical question, of course you do, and with [this voice recognition library](https://www.npmjs.com/package/aframe-speech-command-component) you can! 

```markup
<script src="//cdnjs.cloudflare.com/ajax/libs/annyang/2.5.0/annyang.min.js"></script>
<script src="https://rawgit.com/lmalave/aframe-speech-command-component/master/dist/aframe-speech-command-component.min.js"></script>
<a-scene>
  <a-box id="box" color="red" position="0 0 -1"></a-box>
  <a-entity id="annyang" annyang-speech-recognition></a-entity>
  <a-entity speech-command="
    command: red;
    type: attribute;
    targetElement: #box;
    attribute: color;
    value: red"></a-entity>
  <a-entity speech-command="
    command: blue;
    type: attribute;
    targetElement: #box;
    attribute: color;
    value: blue"></a-entity>
</a-scene>
```

## Webcam Texture

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
  </head>
  <body>
    <a-scene>
      <a-assets>
        <video id="webcam"></video>
      </a-assets>
      <a-videosphere material="src: #webcam"></a-videosphere>
    </a-scene>
    <script>
      // You can also set which camera to use (front/back/etc)
      // @SEE https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
      navigator.mediaDevices
        .getUserMedia({ audio: false, video: true })
        .then(stream => {
          let video = document.querySelector("video");
          video.srcObject = stream;
          video.onloadedmetadata = () => {
            video.play();
          };
        });
    </script>
  </body>
</html>
```

