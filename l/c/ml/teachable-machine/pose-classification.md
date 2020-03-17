# Pose Classification

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

      var leftSound = new Audio(
        "https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fow.mp3"
      );
      var rightSound = new Audio(
        "https://cdn.glitch.com/d4053f1b-1712-446e-85d0-2d353c835228%2Fdog.mp3"
      );

      var leftPlaying = false;
      var rightPlaying = false;

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
            if (label == "left") {
              if (leftPlaying == false) {
                leftSound.play();
                leftPlaying = true;
                rightPlaying = false;
                rightSound.pause();
                rightSound.currentTime = 0;
              }
            } else if (label == "right") {
              if (rightPlaying == false) {
                rightSound.play();
                leftPlaying = false;
                rightPlaying = true;
                leftSound.pause();
                leftSound.currentTime = 0;
              }
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

