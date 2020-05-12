# 11. Conditional Statements

You may have heard of [**If This Then That**](https://ifttt.com/), a tool that combines services using conditional statements eg. if a song is liked on Spotify, send an email. 

Using conditional statements allow us to create multiple paths, and the more paths we provide, the more interesting and unexpected journeys we may have! Once you code a bit you can actually start to think in these logic ways \(think of yourself becoming Vulcan, rather than a machine\)!

## If and Else

```javascript
var isMorning = true;

if (isMorning == true){
    background(0);
} else {
    background(255);
}
```

This statement asks whether the variable **isMorning** is equal to **true**. Since it is, the background will be set to 0. If it would be anything but **true**, it would be set to 255.

Sometimes the situation is not so boolean, and there are more paths that can be taken than simply true or false.

```javascript
var currentHour = 6;

if (currentHour == 6){
    background(0);
} else if (currentHour == 7) {
    background(128);
} else {
    background(255);
}
```

In this case, we check whether the variable **currentHour** is equal to **14** and since it isn't we then ask whether it is equal to **15**, which in our case is true, and so the background will be 128.

When the statement within the parentheses is true, whatever is inside will happen.

It is also possible to have a conditional statement within a range.

```javascript
var currentHour = 6;

if (currentHour > 5 && currenthour < 12){
    background(0);
} else {
    background(255);
}
```

Instead of using the equal sign, we instead use right and left arrows, saying **if the current hour is more than 5 and if the current hour is less than 12**. Since 6 is more than 5, this will be true, and the background will be 0.

* Equal \(==\)
* Not equal \(!=\)
* Greater than \(&gt;\)
* Greater than or equal \(&gt;=\)
* Less than \(&lt;\)
* Less than or equal \(&lt;=\)
* && \(and\)
* \|\| \(or\)

