# Spark AR

Building Augmented Reality experiences for Instagram is possible using Facebook software Spark AR. Through its interface designs for face, neck, eyes, flat surfaces and even custom images can be made!

### Install

Begin by installing the Spark AR \([download](https://sparkar.facebook.com/ar-studio/)\) application.

### [Debugging](https://sparkar.facebook.com/ar-studio/learn/documentation/docs/testing-debugging/)

```javascript
// Load in the Diagnostics module
const Diagnostics = require('Diagnostics');

// Log a string message  
Diagnostics.log('A console message logged from the script');

let myVariable = 5;

// Log a variable's value  
Diagnostics.log(myVariable);
```

Signal values can be shown in the **Console** from within a script with the `watch()` method of the Diagnostics Module.

```javascript
// Load in the required modules
const Diagnostics = require('Diagnostics');
const FaceTracking = require('FaceTracking');

// Add the mouth openness signal to the watch view
Diagnostics.watch("Mouth Openness - ", FaceTracking.face(0).mouth.openness);
```

## Convert FBX to GLTF

a

## [Supported File Formats](https://sparkar.facebook.com/ar-studio/learn/documentation/before-you-start/file-formats/)

### 2D Assets <a id="2d-assets"></a>

* PNG
* JPEG
* SVG

### 3D Models <a id="3d-models"></a>

* FBX 2014/2015 \(binary and ASCII versions\)
* gITF 2 \(binary and text versions\)
* COLLADA / DAE
* OBJ
* DAE

The following features are supported for 3D models:

* 3D scene.
* Materials.
* Textures.
* Animations targeting a model's position, rotation and scale.

### Audio <a id="audio"></a>

* Mono M4A, with a sampling frequency of 44.1kHz

### Fonts <a id="fonts"></a>

* TrueType/ OpenType

