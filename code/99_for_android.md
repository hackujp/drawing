# Step 6. 仕上げ

index.html

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Parcel Sandbox</title>
    <meta charset="UTF-8" />
  </head>

  <body>
    <div id="app"></div>
    <div>
      <button id="clear-button">全消し</button>
    </div>
    <div>
      <canvas
        id="draw-area"
        width="400px"
        height="400px"
        style="border: 1px solid #000000;"
      >
      </canvas>
    </div>

    <script src="src/index.js"></script>
  </body>
</html>
```

src/index.js
```js
import "./styles.css";

const canvas = document.querySelector("#draw-area");
const context = canvas.getContext("2d");

canvas.addEventListener("mousemove", event => {
  draw(event.layerX, event.layerY);
});
canvas.addEventListener("touchmove", event => {
  // draw(event.layerX, event.layerY);
  var touch = event.touches[0];
  var x = touch.pageX - canvas.offsetLeft;
  var y = touch.pageY - canvas.offsetTop;
  event.preventDefault();
  draw(x, y);
});

canvas.addEventListener("mousedown", () => {
  context.beginPath();
  isDrag = true;
});
canvas.addEventListener("mouseup", () => {
  context.closePath();
  isDrag = false;
});
canvas.addEventListener("touchstart", () => {
  context.beginPath();
  isDrag = true;
});
canvas.addEventListener("touchend", () => {
  context.closePath();
  isDrag = false;
});

const clearButton = document.querySelector("#clear-button");
clearButton.addEventListener("click", () => {
  context.clearRect(0, 0, canvas.width, canvas.height);
});

let isDrag = false;
function draw(x, y) {
  if (!isDrag) {
    return;
  }

  context.lineWidth = 5;
  context.lineTo(x, y);
  context.stroke();
}
```
