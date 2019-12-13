# Sound Classification

The [ml5.soundClassifier\(\)](https://learn.ml5js.org/docs/#/reference/sound-classifier) allows you to classify audio. With the right pre-trained models, you can detect whether a certain noise was made or a certain word was said. It is also possible to use the pre-trained speech commands or use the "SpeechCommands18w" which can recognise "the ten digits from "zero" to "nine", "up", "down", "left", "right", "go", "stop", "yes", "no".

{% tabs %}
{% tab title="Clap & Whistle" %}
```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let modelUrl = "https://teachablemachine.withgoogle.com/models/gC-2OI2X/";

      function preload() {
        classifier = ml5.soundClassifier(modelUrl + "model.json", modelReady);
        log = createDiv("Loading model.");
        //classifier = ml5.soundClassifier("SpeechCommands18w", modelReady, options);
      }

      function setup() {
        noCanvas();
      }

      function modelReady() {
        log.html("Model loaded!");
        classifier.classify(gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        let label = results[0].label.toLowerCase();
        let confidence = results[0].confidence;
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);
      }
    </script>
  </body>
</html>

```
{% endtab %}

{% tab title="Trigger Sounds" %}
```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.10.2/addons/p5.sound.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let modelUrl = "https://teachablemachine.withgoogle.com/models/X8jOJwqo/";

      let sounds = [
        {
          label: "mickey",
          url:
            "https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fow.mp3"
        },
        {
          label: "goofy",
          url:
            "https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fdog.mp3"
        },
        {
          label: "minnie",
          url:
            "https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Frooster.mp3"
        }
      ];

      function preload() {
        classifier = ml5.soundClassifier(modelUrl + "model.json", modelReady);

        for (let sound of sounds) {
          sound.isEnabled = false;
          sound.file = loadSound(sound.url);
        }
        log = createDiv("Loading model.");
      }

      function setup() {
        noCanvas();
      }

      function modelReady() {
        log.html("Model loaded!");
        classifier.classify(gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        let label = results[0].label;
        let confidence = results[0].confidence;
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);

        if (confidence > 0.7) {
          for (let sound of sounds) {
            if (sound.label === label) {
              playSound(sound);
            }
          }
        }
      }

      function playSound(sound) {
        if (!sound.file.isPlaying() && !sound.isEnabled) {
          sound.file.play();
          sound.isEnabled = true;
          setTimeout(function() {
            sound.isEnabled = false;
          }, 1000);
        }
        for (let s of sounds) {
          if (s.file !== sound.file) {
            s.file.stop();
          }
        }
      }
    </script>
  </body>
</html>

```
{% endtab %}

{% tab title="Play Sounds" %}
```markup
<html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.3.1/dist/tf.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@teachablemachine/pose@0.8/dist/teachablemachine-pose.min.js"></script>
  </head>
  <body>
    <button type="button" onclick="init()">Start</button>
    <div><canvas id="canvas"></canvas></div>
    <div id="label-container"></div>

    <script>
      const URL = "https://teachablemachine.withgoogle.com/models/qxcZAMrG/";
      let model, webcam, ctx, labelContainer, maxPredictions;

     let sounds = [
        {
          label: "left",
          isPlaying: false,
          file:
            new Audio("https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fow.mp3")
        },
        {
          label: "right",
          isPlaying: false,
          file:
            new Audio("https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fdog.mp3")
        }
      ];

      async function init() {
        const modelURL = URL + "model.json";
        const metadataURL = URL + "metadata.json";

        model = await tmPose.load(modelURL, metadataURL);
        maxPredictions = model.getTotalClasses();

        const size = 200;
        const flip = true;
        webcam = new tmPose.Webcam(size, size, flip);
        await webcam.setup();
        await webcam.play();
        window.requestAnimationFrame(loop);

        const canvas = document.getElementById("canvas");
        canvas.width = size;
        canvas.height = size;
        ctx = canvas.getContext("2d");
        labelContainer = document.getElementById("label-container");
        for (let i = 0; i < maxPredictions; i++) {
          labelContainer.appendChild(document.createElement("div"));
        }
      }

      async function loop(timestamp) {
        webcam.update();
        await predict();
        window.requestAnimationFrame(loop);
      }

      async function predict() {
        const { pose, posenetOutput } = await model.estimatePose(webcam.canvas);
        const prediction = await model.predict(posenetOutput);

        for (let i = 0; i < maxPredictions; i++) {
          var label = prediction[i].className;
          var confidence = prediction[i].probability.toFixed(2);
          if (confidence > 0.9) {
          for 
          if (label == "left"){
          sounds[0].file.play();
          sounds[0].isPlaying = true;
          }
          if (label == "right"){
          sounds[1].file.play();
          }
            if (label == sound.label){
              
            }
          }
            switch (label) {
              case "luggage":
                if (!aPlaying) {
                  a.play();
                  aPlaying = true;
                  bPlaying = false;
                  b.pause();
                  b.currentTime = 0;
                  text.textContent = aText;
                }
                break;
              case "ticket checker":
                if (!bPlaying) {
                  b.play();
                  bPlaying = true;
                  aPlaying = false;
                  a.pause();
                  a.currentTime = 0;
                  text.textContent = bText;
                }
                break;
            }
          }

          const classPrediction = label + ": " + confidence;
          labelContainer.childNodes[i].innerHTML = classPrediction;
        }

        drawPose(pose);
      }

      function drawPose(pose) {
        if (webcam.canvas) {
          ctx.drawImage(webcam.canvas, 0, 0);
          if (pose) {
            const minPartConfidence = 0.5;
            tmPose.drawKeypoints(pose.keypoints, minPartConfidence, ctx);
            tmPose.drawSkeleton(pose.keypoints, minPartConfidence, ctx);
          }
        }
      }

      function playSound(sound) {
        if (!sound.file.isPlaying() && !sound.isEnabled) {
          sound.file.play();
          sound.isEnabled = true;
          setTimeout(function() {
            sound.isEnabled = false;
          }, 1000);
        }
        for (let s of sounds) {
          if (s.file !== sound.file) {
            s.file.stop();
          }
        }
      }
    </script>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

{% hint style="success" %}
The `SpeechCommands18w`  is a JavaScript module that enables recognition of spoken commands comprised of simple isolated English words from a small vocabulary. The default vocabulary includes the following words: the ten digits from "zero" to "nine", "up", "down", "left", "right", "go", "stop", "yes", "no", as well as the additional categories of "unknown word" and "background noise".
{% endhint %}

