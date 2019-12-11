# Step 4. 線を消せるようにしよう

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
  draw(event.layerX, event.layerY);
});

function draw(x, y) {
  context.lineWidth = 5;
  context.lineTo(x, y);
  context.stroke();
}
```

Next: [step05.md](./step05.md)
