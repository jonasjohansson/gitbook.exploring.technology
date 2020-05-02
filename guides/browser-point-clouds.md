# Browser Point Clouds

A point cloud is a collection of points in 3D space. A point can be understood best compared to a pixel in an image, where the pixel has four channels for color RGBA and the point has three channels for position XYZ.

![](../.gitbook/assets/trees.png)

### Install

Download [Metashape](https://www.agisoft.com/) and [CloudCompare](https://cloudcompare.org/).

### Import

#### Video

Go to `File > Import > Import Video…` and select the video file. When asked, create a folder for the extracted frames.

#### Image

Go to `Workflow > Add Folder…` or `Workflow > Add Images…`

### Workflow

The following steps will process the images and create a textured mesh.

1. Go to `Workflow > Align Photos…` and choose Medium accuracy to save time.
2. Once loaded, go to `Workflow > Align Photos…`and choose Medium quality.
3. `Workflow > Build Dense Cloud…`
4. `Workflow > Build Mesh…`
5. `Workflow > Build Texture…`
6. `File > Export > Export model…`
7. Import the model in CloudCompare and `Edit > Mesh > Sample Points` to generate a point cloud.
8. Select the sampled mesh and save as PLY \(binary\)

## Examples

{% tabs %}
{% tab title="Three PLY" %}
```markup
<html>
  <body style="margin: 0;">
    <script type="module">
      import * as THREE from 'https://unpkg.com/three/build/three.module.js';
      import { PLYLoader } from 'https://unpkg.com/three/examples/jsm/loaders/PLYLoader.js';
      import { FlyControls } from 'https://unpkg.com/three/examples/jsm/controls/FlyControls.js';

      const scene = new THREE.Scene();
      const clock = new THREE.Clock();
      const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.01, 10000);

      const renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.body.appendChild(renderer.domElement);

      const controls = new FlyControls(camera, renderer.domElement);
      controls.movementSpeed = 1000;

      new PLYLoader().loader.load('MODEL.ply', function (geometry) {
        let material = new THREE.PointsMaterial({
          vertexColors: THREE.VertexColors,
          size: 1,
          sizeAttenuation: false
        });
        let mesh = new THREE.Points(geometry, material);
        scene.add(mesh);
        animate();
      });

      function animate() {
        requestAnimationFrame(animate);
        controls.update(clock.getDelta());
        renderer.render(scene, camera);
      }
    </script>
  </body>
</html>
```
{% endtab %}

{% tab title="A-Frame PLY" %}
```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script src="https://unpkg.com/aframe-pointcloud-component/dist/aframe-pointcloud-component.min.js"></script>
  </head>
  <body>
    <a-scene background="color: black">
      <a-pointcloud src="url(MODEL.ply)" size="0.01">
      </a-pointcloud>
    </a-scene>
  </body>
</html>
```
{% endtab %}

{% tab title="Three IMG to PLY" %}
```markup
<html>
  <body style="margin: 0;">
    <script type="module">
      import * as THREE from 'https://unpkg.com/three/build/three.module.js';
      import { FlyControls } from 'https://unpkg.com/three/examples/jsm/controls/FlyControls.js';

      const scene = new THREE.Scene();
      const clock = new THREE.Clock();
      const camera = new THREE.PerspectiveCamera(45, window.innerWidth / window.innerHeight, 0.01, 10000);
      camera.position.set(0, 0, 800);

      var renderer = new THREE.WebGLRenderer({ antialias: true });
      renderer.setSize(window.innerWidth, window.innerHeight);
      document.body.appendChild(renderer.domElement);

      var controls = new FlyControls(camera, renderer.domElement);
      controls.movementSpeed = 1000;

      new THREE.TextureLoader().load(
        'https://images.unsplash.com/photo-1507041957456-9c397ce39c97?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=934&q=80',
        texture => {
          var width = Math.round(texture.image.width);
          var height = Math.round(texture.image.height);
          var depth = 50;
          var canvas = document.createElement('canvas');
          canvas.width = width;
          canvas.height = height;
          var ctx = canvas.getContext('2d');
          ctx.drawImage(texture.image, 0, 0);
          var imageData = ctx.getImageData(0, 0, width, height);
          //document.body.appendChild(canvas);

          var geometry = new THREE.BufferGeometry();
          var positions = [];

          var color = new THREE.Color();
          var colors = [];

          for (var y = 0; y < height; y++) {
            for (var x = 0; x < width; x++) {
              let i = x + y * width;
              let j = i * 4;

              let r = imageData.data[j + 0] / 255;
              let g = imageData.data[j + 1] / 255;
              let b = imageData.data[j + 2] / 255;
              let brightness = getBrightness(r, g, b);
              var z = map(brightness, 0, 1, -depth, depth);
              color.setRGB(r, g, b);
              colors.push(color.r, color.g, color.b);
              positions.push(x - height / 2, -y + width / 2, z);
            }
          }

          geometry.setAttribute('position', new THREE.Float32BufferAttribute(positions, 3));
          geometry.setAttribute('color', new THREE.Float32BufferAttribute(colors, 3));
          geometry.computeBoundingSphere();

          var material = new THREE.PointsMaterial({
            size: 1,
            vertexColors: true,
            sizeAttenuation: false
          });

          let mesh = new THREE.Points(geometry, material);
          scene.add(mesh);
          animate();
        }
      );

      function animate() {
        requestAnimationFrame(animate);
        controls.update(clock.getDelta());
        renderer.render(scene, camera);
      }

      const map = (value, x1, y1, x2, y2) => ((value - x1) * (y2 - x2)) / (y1 - x1) + x2;
      const getBrightness = (r, g, b) => (r * 299 + g * 587 + b * 114) / 1000;
    </script>
  </body>
</html>

```
{% endtab %}
{% endtabs %}

