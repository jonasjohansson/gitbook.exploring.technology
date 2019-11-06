# Voice recognition

Do you want to control your visuals through voice? That's a rhetorical question, of course you do, and with the Annyang voice recognition library it's dead simple!

```
<script src="//cdnjs.cloudflare.com/ajax/libs/annyang/2.5.0/annyang.min.js"></script>
<script src="https://rawgit.com/lmalave/aframe-speech-command-component/master/dist/aframe-speech-command-component.min.js"></script>
```

```
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



