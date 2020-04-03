# 10. Conditional Statements

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



