# Magic Grid
## A simple, lightweight Javascript library for dynamic grid layouts.

Creating a dynamic grid layout has never been easier. With Magic Grid, all you have to do is specify a container, and listen for changes. A few other configuration options are available for convenience but it's all very simple.

![demo.gif](https://drive.google.com/uc?id=172ESPZDwQIf7vLMelun-_4RaWD_-j94-)

### Getting Started:
```
npm install magic-grid
```

### Usage:
#### For static content
If your container doesn't have any dynamically loaded content i.e., all its child elements are always in the DOM, you should initialize the grid this way:
```javascript
let magicGrid = new MagicGrid({
  container: "#container", // Required. Can be class or id selector
  static: true, // Required for static content
  animate: true, // Optional
});

magicGrid.listen();
```

#### For dynamic content
If the container relies on data from an api, or experiences a delay, for whatever reason, before it can render its content in the DOM, you need to let the grid know how many items to expect:
```javascript
let magicGrid = new MagicGrid({
  container: "#container", // Required. Can be class or id selector
  items: 20, // For a grid with 20 items. Required for dynamic content
  animate: true, // Optional
});

magicGrid.listen();
```

### API

#### MagicGrid(config)
 > config (required): Configuration object

The MagicGrid constructor. Initializes the grid with a configuration object.
```javascript
let magicGrid = new MagicGrid({
  container: "#container", // Required. Class or id of the container.
  static: "false", // Required for static content. Default: false.
  items: 30, // Required for dynamic content. Initial number of items in the container.
  gutter: 30, // Optional. Space between items. Default: 25(px)
  maxColumns: 5, // Maximum number of colums. Default: Infinite
  useMin: true, // Append next element to the shortest column. Default: false.
  animate: true, // Animate item positioning. Default: false.
});
```

---

#### .listen()
Positions the items and listens for changes to the window size. All items are repositioned whenever the window is resized.
```javascript
let magicGrid = new MagicGrid({
  container: "#container", // Required. Can be class or id selector
  static: true, // Required for static content
  animate: true, // Optional
});

magicGrid.listen();
```

---

#### .positionItems()
This function is useful in cases where you have to manually trigger a repositioning; for instance, if a new element is added to the container

```javascript
let magicGrid = new MagicGrid({
  container: "#container", // Required. Can be class or id selector
  items: 30, // Required for dynamic content.
  animate: true, // Optional
});

magicGrid.listen();

// get new item from api
// append item to dom

// reposition
magicGrid.positionItems();
```

---