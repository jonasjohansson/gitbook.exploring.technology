# API

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

