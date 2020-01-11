# Spark AR

Building Augmented Reality experiences for Instagram is possible using Facebook software Spark AR. Through its interface designs for face, neck, eyes, flat surfaces and even custom images can be made!

* [https://sparkar.facebook.com/ar-studio/learn/documentation/before-you-start/file-formats/](https://sparkar.facebook.com/ar-studio/learn/documentation/before-you-start/file-formats/)

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

## Reduce File size

Since Spark has a file size limit of 4mb models must be reduced in order to fit within the constraints. From the list of supported formats 

![](../../../.gitbook/assets/spark-flowers.png)

The polygon reduction has already helped immensely, reducing the amount of polygons in the scene with up to 90%. Let's see what size the different export options yield.

| Filetype | File size \(mb\) |
| :--- | :--- |
| Flowers.c4d | 14.7 |
| Flowers.obj | 13.3 |
| Flowers.fbx | 4.7 |
| Flowers.gltf | 2.2 |
| Flowers.glb | 1.7 |

