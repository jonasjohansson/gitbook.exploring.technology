# Device API

```markup
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Hello!</title>
    <meta charset="utf-8">
  </head>  
  <body>
    <div id="acc">
    </div>
    
    <script>
      const div = document.getElementById("acc");
      const end = '<br>';

      window.ondevicemotion = function(event) {
        div.innerHTML = 'Acceleration X: ' + event.accelerationIncludingGravity.x + end;
        div.innerHTML += 'Acceleration Y: ' + event.accelerationIncludingGravity.y + end;
        div.innerHTML += 'Acceleration Z: ' + event.accelerationIncludingGravity.z + end;
        if (event.rotationRate) {
          div.innerHTML += 'Rotation Alpha: ' + Math.round(event.rotationRate.alpha) + end;
          div.innerHTML += 'Rotation Beta: ' + Math.round(event.rotationRate.beta) + end;
          div.innerHTML += 'Rotation Gamma: ' + Math.round(event.rotationRate.gamma) + end;
        }
      };

      window.ondeviceorientation = function(event) {
        var alpha = Math.round(event.alpha);
        var beta = Math.round(event.beta);
        var gamma = Math.round(event.gamma);
        div.innerHTML += 'Gyroscope Alpha: ' + Math.round(event.alpha) + end;
        div.innerHTML += 'Gyroscope Beta: ' + Math.round(event.beta) + end;
        div.innerHTML += 'Gyroscope Gamma: ' + Math.round(event.gamma);
        
        document.body.style.backgroundColor = `rgb(${alpha},0,0)`;
      };

    </script>
  </body>
</html>

```

