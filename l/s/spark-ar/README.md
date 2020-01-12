# Spark AR \(draft\)

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

When the console is not available, for instance when testing out on a device, go to Add &gt; 2D Objects &gt; 2D Text. Place the text object and then update its text value in code whenever information needs to be visible.

```javascript
const text = Scene.root.find('2dText0');
text.text = myString;
```

