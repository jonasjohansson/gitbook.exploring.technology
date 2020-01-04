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
        createCanvas(640, 480);
        video = createCapture(VIDEO);
        video.size(width, height);
        poseNet = ml5.poseNet(video, modelReady);
        poseNet.on("pose", function(results) {
          poses = results;
        });
        video.hide();
      }

      function modelReady() {}

      function mousePressed() {
        console.log(JSON.stringify(poses));
      }

      function draw() {
        image(video, 0, 0, width, height);

        if (poses.length > 0) {
          let pose = poses[0].pose;
        }
      }
    </script>
  </body>
</html>
```

