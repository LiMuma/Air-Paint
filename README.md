# Air Paint

Dip your finger in a little color. Paint a little joy in the air.

An interactive air-painting web app with camera-based hand tracking, flowing paint, and drip effects. Create with hand gestures, a mouse, or touch.

**[Try Air Paint](https://limuma.github.io/Air-Paint/)**

## Features

- Paint over a mirrored live camera scene or a textured wall background.
- Control color, brush size, water amount, fluidity, drip length, and drip thickness.
- Watch wet paint develop and drip while you draw; repeated strokes add more paint.
- Use hand gestures without a calibration step, or draw with a mouse or touchscreen.
- Erase locally, undo the last operation, clear the canvas, and export a PNG.

## How to Use

1. Open [Air Paint](https://limuma.github.io/Air-Paint/) in a browser.
2. Click the camera button and allow camera access, or drag on the canvas with a mouse or finger.
3. Keep your whole hand visible, with good lighting, when using gesture controls.
4. Export your artwork before refreshing or closing the page.

The current interface is in Chinese. The main controls are:

| Control | Meaning |
| --- | --- |
| 开启摄像头 | Enable camera |
| 加水量 | Water amount: more water makes paint more transparent |
| 流动性 | Fluidity: controls how quickly paint flows |
| 画笔粗细 | Brush size |
| 滴流长度 | Drip length |
| 滴流粗细 | Drip thickness |
| 手部防抖 | Hand smoothing |
| 橡皮大小 | Eraser size |
| 撤销 | Undo |
| 清空 | Clear |
| 导出 PNG | Export PNG |

## Gesture Controls

| Gesture | Action |
| --- | --- |
| Extend your index finger toward the camera, keeping other fingers curled | Draw |
| Point your index finger upward, keeping other fingers curled | Draw |
| Open all five fingers | Lift the brush without drawing |
| Make a fist and move your hand | Erase around the palm position |
| Move your hand out of view | Stop drawing |

Tracking may be less reliable when fingers overlap, the hand is partly outside the frame, or lighting is poor.

## Run Locally

Download this repository with **Code → Download ZIP**, then extract it.

The app is bundled into a single `index.html` file. No npm install or build step is required. You can open the file to try mouse or touch drawing; camera access from a local file depends on your browser.

For more reliable camera access, run a local server from the folder containing `index.html`:

```sh
python3 -m http.server 3000
```

Then open [http://localhost:3000](http://localhost:3000).

Camera access requires permission and a browser-supported secure context, such as HTTPS or localhost. An ordinary HTTP address on your local network may not permit camera access.

## Phones and Tablets

Use the hosted HTTPS link rather than opening the HTML file through a file preview. Try Safari on iPhone or iPad, or Chrome on Android. If an in-app browser cannot access the camera, open the link in your regular browser.

Touch drawing is supported. Camera tracking and performance depend on the device and browser; this version has not yet been verified on physical phones or iPads.

## Technology

- HTML and CSS for the interface.
- JavaScript and Canvas 2D for paint, texture, dripping, and compositing.
- MediaPipe Hands for hand landmark detection.

The paint is a procedural visual simulation, not a full fluid-physics solver. Camera painting is a 2D overlay: strokes stay in screen coordinates, without 3D anchoring or real-world object occlusion.

## Privacy and Connectivity

Camera frames are processed locally in your browser. The app does not upload camera video.

Hand tracking loads MediaPipe code and model assets from a third-party CDN. An internet connection is required when these assets are not cached. The app is not guaranteed to work fully offline.

Artwork is not automatically saved. Refreshing or closing the page clears it; use PNG export to keep a copy.
