# Variables

Programming uses “variables” to pass information effectively. Imagine that you want to create a circle and a rectangle. The rectangle must have its width and height be half of the circle diameter. You could “hard code” it in like this:

```javascript
circle(100,100,200);
rect(0,0,100,100);
```

Or you could use a variable:

```javascript
var diameter = 200;
circle(100,100,diameter);
rect(0,0,diameter/2,diameter/2);
```

Variables are initiated by typing "var" or "let" followed by the name of the variable. Names should follow the English Alphabet,  avoiding numbers and special characters. If your variable has several words, try to type it in "camel case", for instance **myNewFunction**.

Notice that the variables are sometimes inside of a function, such as diameter, and sometimes outside in the top. This is has to do with something called “scope”. Anything that is declared at the top is “global”, meaning it can be accessed from anywhere in the code. In the example here “diameter” is local, and can only be read from within the draw-function. In most cases you can use global variables, but it is good practice to only have variables be available where they are needed.

```javascript
var global = "I am available everywhere!";

function setup(){
    var local = "I'm only available in here…";
}

function draw(){
    println(global); // this will work
    println(local); // this will not
}
```

## 

