# API

```markup
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    
    <!-- import the webpage's stylesheet -->
    <link rel="stylesheet" href="/style.css">
    
    <!-- import the webpage's javascript file -->
    <script src="/script.js" defer></script>
  </head>  
  <body>
    <h1>Hi there!</h1>
´

<script>
    const url = "https://api.giphy.com/v1/gifs/trending?api_key=HRhpcL0IBoSbV4A2wvunhToa6XsPIzNg&limit=25&rating=G"

    fetch(url)
        .then(resp => resp.json())
        //.then(resp => resp.text())
        // .then(responseBody => new window.DOMParser().parseFromString(responseBody, 'text/xml'))
        .then(responseBody => {
            console.log(responseBody);
        });

</script>
  </body>
</html>

```



```markup
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>  
  <body>
    
    <div id="data">
      HELLO
    </div>
    

    <script>
        const url = `https://api.met.no/weatherapi/locationforecastlts/1.3/?lat=${55.6704726}&lon=${13.1226753}`;
        fetch(url)
            .then(response => {
                return response.text();
            })
            .then(responseBody => new window.DOMParser().parseFromString(responseBody, 'text/xml'))
            .then(responseBody => {
                var windSpeed = responseBody.getElementsByTagName('windSpeed')[0].getAttribute('mps');
                var data = document.querySelector("#data");      
                data.innerHTML = windSpeed; 
                data.style.fontSize = (windSpeed*10)+'px';
            });

    </script>
  </body>
</html>

```



## Magnetometer

```markup
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
  </head>  
  <body>
    <div id="status">
      asd
    </div>
    <script>
       var sensor = new Magnetometer();
        sensor.addEventListener('reading', function(e) {
          document.getElementById('status').innerHTML = 'x: ' + e.target.x + ' y: ' + e.target.y + ' z: ' + e.target.z;
        });
        sensor.start();
    </script>
  </body>
</html>

```

