# Logic

We use logic to tell the code what to do in specific situations. For instance, if the mouse is clicked, or a number reaches a certain value. Once you code a bit you can actually start to think in these logic ways \(think of yourself becoming Vulcan, rather than a machine\)!  
The most common logical statements are:

* If
* If/Else
* For

You will use these no matter the coding syntax or language, or level of advancement, as it’s pure logic!

### If

“If” is your bread and butter, so you better learn it well. It looks like this:

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

An addition to “if”, used like this:

```javascript
var myVariable = 3;
if (myVariable == 2){
 background(0,255,0);
} else {
 background(255,0,0);
}
```

You can include more conditions by adding "else if" between "if" and "else":

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

Let’s say you want to create three circles, each a bit smaller than the previous one, you could do this:

```javascript
circle(200,200,150);
circle(200,200,100);
circle(200,200,50);
```

But you could also do this:

```javascript
var numberOfCircles = 3;
for (i = 0; i < numberOfCircles; i++){
    diameter = 150 - (i * 50)
    circle(200,200,diameter);
}
```

As long as the statement is true, whatever is inside the curly brackets will happen. It starts with defining a variable, in this case “i” with the value of 0. And then continues by saying that “as long as x is less than 3, increment i with 1. This will happen until i reaches 2, after which it will exit the for loop.

![](https://lh6.googleusercontent.com/ZuCd82ST3Ypfa0O3oR-LlAyP_ax_fwnqpsVOaph3vaQMj2baSFObwhEVpU8IQnnJBDSRwsd6SWxe5gEDy64RnY2C2rt-oqcFeVjc3i_5RfmCWb5Y1vzg04dq68iTCu7K7Sgd72cQi-I)

Imagine you wanted to do 1000 circles, you can quickly see the benefit of a for loop.

