# Image Classification

You can use neural networks to recognise the content of images. [ml5.imageClassifier\(\)](https://learn.ml5js.org/docs/#/reference/image-classifier) is a method to create an object that classifies an image using a pre-trained model.

It should be noted that the pre-trained model provided by the example below was trained on a database of approximately 15 million images \(ImageNet\). The ml5 library accesses this model from the cloud. What the algorithm labels an image is entirely dependent on that training data -- what is included, excluded, and how those images are labeled \(or mislabeled\).

```markup
<html>
  <head>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/p5.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.9.0/addons/p5.dom.min.js"></script>
    <script src="https://unpkg.com/ml5@0.4.3/dist/ml5.min.js"></script>
  </head>
  <body>
    <script>
      let classifier;
      let imageModelURL =
        "https://teachablemachine.withgoogle.com/models/H1sVtfEK/";

      let log, video;

      function setup() {
        noCanvas();
        log = createDiv("Loading model.");
        video = createCapture(VIDEO);
        classifier = ml5.imageClassifier(
          imageModelURL + "model.json",
          //'MobileNet',
          video,
          modelReady
        );
      }

      function modelReady() {
        log.html("Model loaded!");
        classifyVideo();
      }

      function classifyVideo() {
        classifier.classify(gotResult);
      }

      function gotResult(error, results) {
        if (error) {
          console.error(error);
          return;
        }
        let label = results[0].label.toLowerCase();
        let confidence = nf(results[0].confidence, 0, 2);
        log.html(`Label: ${label} <br>Confidence: ${confidence}`);
        classifyVideo();
      }
    </script>
  </body>
</html>
```

