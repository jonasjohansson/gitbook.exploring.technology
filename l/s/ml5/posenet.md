---
description: 'https://ml5js.org/reference/api-PoseNet/'
---

# PoseNet

```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let video;
      let poseNet;
      let poses = [];

      function setup() {
        createCanvas(320, 240);
        video = createCapture(VIDEO);
        video.size(width, height);
        poseNet = ml5.poseNet(
          video,
          {
            imageScaleFactor: 0.3,
            outputStride: 16,
            flipHorizontal: false,
            minConfidence: 0.8, // 0.5
            maxPoseDetections: 1, // 5
            scoreThreshold: 0.5,
            nmsRadius: 20,
            detectionType: "single",
            multiplier: 0.75
          },
          modelReady
        );
        poseNet.on("pose", function(results) {
          poses = results;
        });
        video.hide();
      }

      function modelReady() {}

      function mousePressed() {
        console.dir(poses);
      }

      function draw() {
        image(video, 0, 0, width, height);

        if (poses.length > 0) {
          let pose = poses[0].pose;

          let nose = pose["nose"];
          ellipse(nose.x, nose.y, 10, 10);

          let rightEye = pose["rightEye"];
          ellipse(rightEye.x, rightEye.y, 10, 10);

          let leftEye = pose["leftEye"];
          ellipse(leftEye.x, leftEye.y, 10, 10);
        }
      }
    </script>
  </body>
</html>
```

