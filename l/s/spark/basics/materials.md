# Materials

Materials in Spark can have different shader types:

1. Flat
2. Standard
3. Physically-Based
4. Face Paint
5. Blended
6. Retouching

Each type comes with its own set of parameters and therefore also script references \([link](https://sparkar.facebook.com/ar-studio/learn/documentation/reference/classes/shadersmodule)\). To update the shader we update its input texture.

```javascript
  var r = Math.random();
  var g = Math.random();
  var b = Math.random();

  var col = R.pack4(r, g, b, 0.5);
  const textureSlot = S.DefaultMaterialTextures.DIFFUSE;

  object.material.setTexture(col, { textureSlotName: textureSlot });
```

### Links

* [https://stackoverflow.com/questions/59683552/tweening-colors-on-spark-ar-via-script](https://stackoverflow.com/questions/59683552/tweening-colors-on-spark-ar-via-script)
* [https://stackoverflow.com/questions/58054968/changing-material-colours-using-script-in-spark-ar](https://stackoverflow.com/questions/58054968/changing-material-colours-using-script-in-spark-ar)

