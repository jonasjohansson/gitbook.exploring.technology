# Bonus - Advanced CHOPs

You've probably had some good fun by now using our psycho-animatic rainbow riding triangle. 

Though probably if you're a bit like me, there's one thing that has been really bugging you. If that's the case, then this bonus task is one for you.

Lets make our triangle rotate along with its direction.

### Lag and offset

In order to calculate this, we will need to know where the triangle is and where it came from. The difference between these two places gives us a direction vector that we can use to calculate the rotation.

An easy way to so this, is by adding a Lag CHOP. Since I like the laggy behavior, lets connect it in between our Merge and our position Null.

Click on the Lag CHOP and set both Lag values to 1.

The added benefit now, is that our Triangle is less jumpy and feels a bit like it has some physics applied to it \(the Spring CHOP is also a good tool for that\).

To calculate the offset, we need to subtract the current position from our lagged position.

Create a Math CHOP and connect it behind the position Null.

Create a second connection between the Merge CHOP and our new Math CHOP.

Select the Math CHOP and set Combine CHOP's to Subtract.

### Calculating the rotation

A regular Math CHOP won't do what we need to calculate the angle itself, this is done using a mathematical function called `Atan2()`. Luckily we have this in the Function CHOP. This one requires both values to come in separately.

Create a Select CHOP and connect it to our Math CHOP. Set its Channel names to tx. 

Repeat this process for ty.

Create a Function CHOP and connect both Select CHOPs.

Select the Function CHOP and set its Function parameter to `atan2(y, x) Arctan( Input1 / Input2 )`.

![](../../../.gitbook/assets/image%20%2812%29.png)

We're almost there, the only thing we need to do is add a rotation of 90 degrees on top of what we get from the Function CHOP.

Add a Math CHOP and under Multi-Add, set Post-Add to 90.

To tidy things up we should rename tx to something nicer, and add a null in the end.

Add a Rename CHOP and set its To parameter to `rotation`.

Add a Null CHOP and call it `rotation`.

### Connect to Parameter

Lets add our result.

Select the first Composite TOP and under Transform connect the rotation CHOP value to our Rotate parameter.



