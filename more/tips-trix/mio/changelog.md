# Changelog

## 1.1.10 - 20200129

Added [syntax from RobotJS](https://robotjs.io/docs/syntax) to accommodate for more mouse events such as mouseScroll.

## 1.1.9 - 20200118

Based on [this](https://github.com/electron/electron/issues/10078) thread.

```javascript
app.dock.hide();
win.setAlwaysOnTop(true, "floating");
win.setVisibleOnAllWorkspaces(true);
win.setFullScreenable(false);
app.dock.show();
```

### Fixed

* Mio works when other apps are fullscreen.



