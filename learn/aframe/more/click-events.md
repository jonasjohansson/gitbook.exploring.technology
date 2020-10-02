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
      <a-box
        cursor-listener="url: https://jonasjohansson.se"
        position="-2 0 -4"
      ></a-box>
      <a-box
        cursor-listener
        animation__mouseenter="property: rotation; startEvents: mouseenter; to: 360 0 360"
        animation__mouseleave="property: rotation; startEvents: mouseleave; to: 0 0 0"
        position="0 0 -4"
      ></a-box>
      <a-box
        cursor-listener
        animation__mouseenter="property: scale; startEvents: mouseenter; to: 2 2 2"
        animation__mouseleave="property: scale; startEvents: mouseleave; to: 1 1 1"
        position="2 0 -4"
      ></a-box>
      <a-entity camera wasd-controls look-controls>
        <a-entity cursor></a-entity>
      </a-entity>
    </a-scene>
  </body>
</html>

```

