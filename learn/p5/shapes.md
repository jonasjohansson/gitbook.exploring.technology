# 1. Shapes

Processing gives you the option to draw all kinds of shapes, but let us begin with the basics.

### Circle

Draw a circle using  `circle(x, y, diameter)`.

```javascript
circle(200, 200, 300);
```

The first two values tell the circle where to be positioned, while the third  defines the size. With the default canvas size of **400 pixels**, the circle will be placed in the middle, since the circle point of origin is its centre.

![](../../.gitbook/assets/p5-circle.png)

### Square

Besides circles we can also add a `square(x, y, size)`. After the circle, make a new line by pressing Enter, then type…

```javascript
square(200, 200, 200);
square(0, 0, 200);
```

The values for the square are similar to that of the circle, however, squares have their point of origin in their top left corner, which is why they are not placed in the middle of the canvas.

![](../../.gitbook/assets/p5-rect.png)

### Related links

* [circle\(\)](https://p5js.org/reference/#/p5/circle)
* [square\(\)](https://p5js.org/reference/#/p5/square)
* [ellipse\(\)](https://p5js.org/reference/#/p5/ellipse)
* [rect\(\)](https://p5js.org/reference/#/p5/rect)

