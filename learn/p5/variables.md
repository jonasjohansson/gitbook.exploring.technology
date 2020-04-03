# 7. Variables

Programming uses “variables” to pass information effectively. Imagine that you want to create a circle and a rectangle. The rectangle must have its width and height be half of the circle diameter. You could “hard code” it in like this:

```javascript
circle(100, 100, 200);
square(0, 0, 100);
```

Or you could use a variable:

```javascript
var diameter = 200;
circle(100, 100, diameter);
square(0, 0, diameter / 2);
```

Variables are initiated by typing **var** or **let** followed by the name of the variable. Names should follow the English Alphabet,  avoiding numbers and special characters. If your variable has several words, type it in "camel case", for instance **myVariable** instead of **myvariable**.

## Predefined variables

There are also predefined variables which are great to play with!

|  |  |
| :--- | :--- |
| [frameCount](https://p5js.org/reference/#/p5/frameCount) | Increases by one on every frame |
| windowWidth | Width of the window |
| windowHeight | Height of the window |
| width | Canvas width |
| height | Canvas height |
| mouseX | Mouse x position |
| mouseY | Mouse y position |

## Scope

Notice that the variables are sometimes inside of a function, such as diameter, and sometimes outside in the top. This is has to do with something called “scope”. Anything that is declared at the top is “global”, meaning it can be accessed from anywhere in the code. In the example here “diameter” is local, and can only be read from within the draw-function. In most cases you can use global variables, but it is good practice to only have variables be available where they are needed.

```javascript
var global = "I'm Global, and I am available everywhere!";

function setup(){
    var local = "I'm Local, and I am only available in here…";
}

function draw(){
    print(global); // this will work
    print(local); // this will not
}
```

## Print

Noticed the `print()` function above? It is a fantastic tool for debugging and letting the programmer know what is going on. Provide it with a variable, and it will print out to the console the value of that variable. This is useful when the variable contains information that is changing fast, or when there are different "states" within your program.

