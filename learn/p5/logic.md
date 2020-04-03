# 9. Logic

We use logic to tell the code what to do in specific situations. For instance, if the mouse is clicked, or a number reaches a certain value. Once you code a bit you can actually start to think in these logic ways \(think of yourself becoming Vulcan, rather than a machine\)!

The most common, bread and butter, logical statements are **if**, **if/else** and **for**. You will use these no matter the coding syntax or language, or level of advancement, as it’s pure logic!

### If

```javascript
var myVariable = 2;
if (myVariable == 2){
 background(0,255,0);
}
```

When the statement within the parentheses is true, whatever is inside will happen. The “==” is a comparison operator meaning “equal”, and there are others:

* Equal \(==\)
* Not equal \(!=\)
* Greater than \(&gt;\)
* Greater than or equal \(&gt;=\)
* Less than \(&lt;\)
* Less than or equal \(&lt;=\)
* Strict equal \(===\)

### **If/else**

```javascript
var myVariable = 3;
if (myVariable == 2){
 background(0,255,0);
} else {
 background(255,0,0);
}
```

You can include more conditions by adding **else if** :

```javascript
var myVariable = 4;
if (myVariable == 2){
 background(0,255,0);
} else if (myVariable == 3) {
 background(255,0,0);
} else {
 background(0,0,255);
}
```

### For

When you want to create three circles, each a bit smaller than the previous one, you could do this:

```javascript
circle(200,200,150);
circle(200,200,100);
circle(200,200,50);
```

But you could also do this:

```javascript
for (i = 0; i < 3; i++) {
  diameter = 150 - (i * 50)
  circle(200, 200, diameter);
}
```

As long as the statement is true, whatever is inside the curly brackets will happen. It begins with defining a variable, in this case "i" with the value of 0. And then continues by saying that “as long as x is less than 3, increment i with 1. This will happen until i reaches 2, after which it will exit the for loop.

![](../../.gitbook/assets/p5-for.png)

{% hint style="danger" %}
Be mindful of Auto-refresh while working with loops as the sketch can get stuck in an infinite cycle, which will crash the browser or cause it to freeze.
{% endhint %}

