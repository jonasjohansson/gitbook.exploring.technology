# Shapes

It is possibly to draw all kinds of vector shapes; circles, squares, rectangles, lines and curves.

Let us begin drawing by adding a circle. The circle function takes three parameters: x, y and diameter. Type the following **inside draw**:

```javascript
circle(200,200,300);
```

The first two values tell the circle where to be, and the last provides the diameter.  In our case, this will place the circle in the middle of the canvas, as the circle has its centre as point of origin. In this situation 200 pushes the circle centre from the left and top.

![](../../../../.gitbook/assets/p5-circle.png)

It is highly recommended to read up on each function using the Processing References, as they are not all the same.

Besides circles we can also add squares. After the circle line, make a new line by pressing Enter, then type:

```javascript
square(200, 200, 200);
square(0, 0, 200);
```

The first two values here are just like the circle, defining x and y, or, the distance from the left and top. However, squares do not have their point of origin in the centre, instead they "start" at their top left.

![](../../../../.gitbook/assets/p5-rect.png)

