# Animation

```javascript
const A = require("Animation");

let baseDriver = A.timeDriver({
    durationMilliseconds: 1000,
    loopCount: 1, // Infinity
    mirror: false
  });
  
  baseDriver.start();
  A.samplers.easeOutQuint(0, 1); // from, to
  
  let val = A.animate(baseDriver, baseSampler);
  
  object.transform.scaleX = val;
  object.transform.scaleY = val;
  object.transform.scaleZ = val;
  object.material.opacity = val;

  baseDriver.onCompleted().subscribe(function() {
      Diagnostics.log("Animation completed!");
  });
```

