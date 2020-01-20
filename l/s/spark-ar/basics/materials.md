# Materials

## Update texture during runtime

```javascript
  var r = Math.random();
  var g = Math.random();
  var b = Math.random();

  var col = R.pack4(r, g, b, 0.5);
  const textureSlot = S.DefaultMaterialTextures.DIFFUSE;

  object.material.setTexture(col, { textureSlotName: textureSlot });
```

* [https://stackoverflow.com/questions/58054968/changing-material-colours-using-script-in-spark-ar](https://stackoverflow.com/questions/58054968/changing-material-colours-using-script-in-spark-ar)

## Tween multiple colours

{% embed url="https://stackoverflow.com/questions/59683552/tweening-colors-on-spark-ar-via-script" %}



