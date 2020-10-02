# Click Events

[https://aframe.io/docs/1.0.0/components/cursor.html](https://aframe.io/docs/1.0.0/components/cursor.html)

```markup
<html>
  <head>
    <script src="https://unpkg.com/aframe@latest"></script>
    <script>
      AFRAME.registerComponent("cursor-listener", {
        schema: {
          url: { type: "string", default: "" }
        },
        init: function() {
          const url = this.data.url;
          this.el.addEventListener("click", function(evt) {
            this.setAttribute("material", "color", "purple");
            if (url !== "") window.location.href = url;
          });
          this.el.addEventListener("mouseenter", function(evt) {
            this.setAttribute("material", "color", "black");
          });
          this.el.addEventListener("mouseleave", function(evt) {
            this.setAttribute("material", "color", "gray");
          });
        }
      });
    </script>
  </head>
  <body>
    <a-scene>
      <a-box cursor-listener color="red" position="-2 0 -2"></a-box>
      <a-box
        cursor-listener="url: https://jonasjohansson.se"
        color="green"
        position="0 0 -2"
      ></a-box>
      <a-box cursor-listener color="blue" position="2 0 -2"></a-box>
      <a-entity camera wasd-controls look-controls>
        <a-entity cursor></a-entity>
      </a-entity>
    </a-scene>
  </body>
</html>

```

