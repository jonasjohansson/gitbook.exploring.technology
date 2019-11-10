# Interaction

Events are fantastic, and P5.js announces several of them which you can tap into. For instance if the Enter button is pressed, or a mouse is clicked… even if your phone is moved!

Let’s check out smartphone interaction.

If you access the sketch \(in presentation view\) through your phone you can use some special variables that contain accelerometer and gyroscope data from your phone, let’s try it out:

```javascript
r = map(rotationX, -90, 90, 0, 255);
g = map(rotationY, -90, 90, 0, 255);
b = map(rotationZ, -90, 90, 0, 255);
background(r,g,b);
```

We are also introducing a function here called “map” which maps one range of values to another. Since the rotation is anything from -90 to 90 \(this could differ, best to check with print!\), and RGB values are 0 to 255, we can use the map function to convert the rotation to a colour value.  
There’s a large list of events that you can use, [check them out and play around](https://p5js.org/reference/#group-Events).



![](https://lh6.googleusercontent.com/A5en_EN677r7gfUWVn1QMiUrbf1pBOb2SdciMz_P8mir0lTgdSJPcCbfn8d69PDhpjpCcz1tWtf4uVlC3wqa9Bh67JmY_8zJ-8PCy3WoWRKzuLkE1QBryAcL1nAO-NsNtcf69wuHfTk)

