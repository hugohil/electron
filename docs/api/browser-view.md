## Class: BrowserView

> Create and control views.

**Note:** The BrowserView API is currently experimental and may change or be
removed in future Electron releases.

Process: [Main](../glossary.md#main-process)

A `BrowserView` can be used to embed additional web content into a
`BrowserWindow`. It is like a child window, except that it is positioned
relative to its owning window. It is meant to be an alternative to the
`webview` tag.

## Example

```javascript
// In the main process.
const {BrowserView, BrowserWindow} = require('electron')

let win = new BrowserWindow({width: 800, height: 600})
win.on('closed', () => {
  win = null
})

let view = new BrowserView({
  webPreferences: {
    nodeIntegration: false
  }
})
win.addChildView(view)
view.setBounds(0, 0, 300, 300)
view.webContents.loadURL('https://electron.atom.io')
```

### `new BrowserView([options])` _Experimental_

* `options` Object (optional)
  * `webPreferences` Object (optional) - See [BrowserWindow](browser-window.md).

### Instance Properties

Objects created with `new BrowserView` have the following properties:

#### `view.webContents` _Experimental_

A [`webContents`](web-contents.md) object owned by this view.

#### `win.id` _Experimental_

A `Integer` representing the unique ID of the view.

### Instance Methods

Objects created with `new BrowserWindow` have the following instance methods:

#### `win.setAutoResize(options)` _Experimental_

* `options` Object
  * `width`: If `true`, the view's width will grow and shrink together with
    the window. `false` by default.
  * `height`: If `true`, the view's height will grow and shrink together with
    the window. `false` by default.

#### `win.setBounds(bounds)` _Experimental_

* `bounds` [Rectangle](structures/rectangle.md)

Resizes and moves the view to the supplied bounds relative to the window.

#### `win.setBackgroundColor(color)` _Experimental_

* `color` String - Color in `#aarrggbb` or `#argb` form. The alpha channel is
  optional.
