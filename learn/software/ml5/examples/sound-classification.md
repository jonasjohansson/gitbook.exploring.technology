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
      let options = {
        probabilityThreshold: 0.9
      };
      let log;
      
      function preload() {
        classifier = ml5.soundClassifier(
          modelUrl + "model.json",
          modelReady,
          options
        );
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
        let label = results[0].label;
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
      let options = {
        probabilityThreshold: 0.9
      };

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
        classifier = ml5.soundClassifier(
          modelUrl + "model.json",
          modelReady,
          options
        );

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
{% endtabs %}

{% hint style="success" %}
The `SpeechCommands18w`  is a JavaScript module that enables recognition of spoken commands comprised of simple isolated English words from a small vocabulary. The default vocabulary includes the following words: the ten digits from "zero" to "nine", "up", "down", "left", "right", "go", "stop", "yes", "no", as well as the additional categories of "unknown word" and "background noise".
{% endhint %}

