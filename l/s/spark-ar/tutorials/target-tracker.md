# Target Tracker

* [https://sparkar.facebook.com/ar-studio/learn/documentation/tracking-people-and-places/target-best-practice/](https://sparkar.facebook.com/ar-studio/learn/documentation/tracking-people-and-places/target-best-practice/)
* [https://sparkar.facebook.com/ar-studio/learn/documentation/tracking-people-and-places/effects-in-surroundings/creating-a-target-ar-effect/](https://sparkar.facebook.com/ar-studio/learn/documentation/tracking-people-and-places/effects-in-surroundings/creating-a-target-ar-effect/)

### Track TargetTracker

* [https://sparkar.facebook.com/ar-studio/learn/documentation/reference/classes/patchesmodule/](https://sparkar.facebook.com/ar-studio/learn/documentation/reference/classes/patchesmodule/)

```javascript
const P = require("Patches");
var trackerFound = P.getBooleanValue("trackerFound");

trackerFound.monitor().subscribe(function(e) {
  Diagnostics.log(e.newValue);
});

```

![](../../../../.gitbook/assets/spark-tracker.png)

