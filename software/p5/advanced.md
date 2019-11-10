# Advanced

## **Variables**

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

## **Logic**

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

### **Combining variables and logic**

Let’s combine the logic and variables using the interactive function `mouseClicked()`. Here we initiate a combination of global variables, which are used in the draw function, but set in the `mouseClicked()` function. MouseClicked is “called” when someone clicks with the mouse in the preview area.

First it checks if the variable “r” is equal to 0, and it does this by three equal signs. Why? Because 0 could also mean false, but in this case we only want to check whether “r” is equal to the number zero. This is called a “strict equal”.

The next time there is a click, it will instead go to the “else” part of the function, and make the background blue.

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


## **Sound**

Playing sound is simple and fun, and can easily be used together with the statements and variables from before. [Let’s look at the example provided by P5.js](https://p5js.org/examples/sound-load-and-play-sound.html).

There’s a lot you can do with sound in P5.js, like building your own instrument!

[Check out the reference guide and see what’s possible.](https://p5js.org/reference/#/libraries/p5.sound)

And remember to look at Daniel Schiffman’s tutorials on Youtube and generally search around for advice and tutorials.

On mobile music needs to be triggered by an event before it is played  


![](https://lh3.googleusercontent.com/kKqiOyxoZGIFKrplLCfUARaJ2JPoqMRqK308TRCXHjYGz_qDPJSLTw5QxVgaYiPM8M4zG2pR0MD45ch27LY0eNghBWMsV-RULoN9S0B0CIOIPen5qDUTBVDIQ1pwCTsF6hXaka_4ejs)

## **Interaction**

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

## **API**

There are many sources that provide interesting data, actually, [here’s a list](https://github.com/public-apis/public-apis)… but to demonstrate the usage we will work with [OpenWeatherMap](https://openweathermap.org) which provide us with weather data! In this example we will use a “key” that someone else has registered, so please get an account and get your own free key. Let’s check out an example:  
****

```javascript
var weather;

function preload() {
 weather = loadJSON("https://api.openweathermap.org/data/2.5/weather?q=Stockholm&units=metric&APPID=8bc33b55474e0525d2c28707ca934965&");
}

function setup() {
 print(weather);
}

function draw() {
 textSize(32);
 text(weather.main.temp, 10, 30);
}
```

We create a variable called “weather”, and then use the preload function which ensures us that the weather data has been loaded before anything else happens.  


![](https://lh4.googleusercontent.com/EDKxDL2fPp1LCY1FDb7t_7KudVEoZnLa4M9eiaVs_OZkd9SnhWxlG_YrOSJED7XXMnkh_StIZtAxcvs_2K5bkN1yg9aFe08zTgp3OsHFl6XFpocyys0hxasJBiDdc3woBUoyI2YE6qA)

