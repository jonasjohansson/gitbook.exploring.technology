# Events

In code, events can be "listened" too. For markers, it is often interesting to learn when they have been found and lost, and create an action.

The script below will register a component which when used will play all video and sound when a marker is found, and pause them when lost. It is used by adding `marker-toggle` to the `<a-marker>` entity.

```markup
<script>
	AFRAME.registerComponent('marker-toggle', {
		init: function () {
			var marker = this.el
			marker.addEventListener('markerFound', function () {
				document.querySelectorAll('video').forEach(el => el.play())
				document.querySelectorAll('[sound],a-sound').forEach(el => el.components.sound.playSound())
			})
			marker.addEventListener('markerLost', function () {
				document.querySelectorAll('video').forEach(el => el.pause())
				document.querySelectorAll('[sound],a-sound').forEach(el => el.components.sound.pauseSound())
			})
		}
	})
</script>
```

And then you can add a special entity to the `<a-marker>`.

```markup
<a-marker marker-toggle>
  <a-video src="#video"></a-video>
</a-marker>
```

