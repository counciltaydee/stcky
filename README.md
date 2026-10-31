# stcky

A starter web app for generating a stickman lip-sync video preview from uploaded audio.

## What this starter includes

- Browser-based UI built with **HTML/CSS/JavaScript** (Vite scaffold)
- Audio upload flow for **mp3, wav, ogg, m4a**
- Canvas-rendered stickman scene with audio-reactive mouth + simple body motion
- Play/pause/restart controls with live timeline preview
- Starter export pipeline:
  - implemented: **WebM** export via `MediaRecorder` (canvas, with audio when the browser supports audio `captureStream()`)
  - documented path to **MP4** via **WebCodecs + MP4Box.js** or **ffmpeg.wasm** conversion

## Setup

```bash
npm install
npm run dev
```

Open the local URL shown by Vite (typically `http://localhost:5173`).

## Build for production

```bash
npm run build
npm run preview
```

## Usage

1. Upload an audio file (`.mp3`, `.wav`, `.ogg`, `.m4a`).
2. Click **Play** to preview stickman lip-sync animation.
3. Click **Pause** or **Restart** as needed.
4. Click **Export WebM (starter)** to download a recorded preview.
5. Use the **MP4 export path** note in the UI as the next implementation step.

### Browser requirements

Preview playback uses the Web Audio API. WebM export additionally requires
`MediaRecorder` and canvas `captureStream()`. The recorder adds the audio track
only when the browser provides `HTMLMediaElement.captureStream()` (or
Firefox's `mozCaptureStream()`), so a browser without audio capture support may
produce a video-only WebM. MP4 export is not implemented; the UI describes the
WebCodecs/MP4Box.js and ffmpeg.wasm options based on browser support.

## Developer notes

The app has no test or lint script in `package.json`; use the Vite scripts for
local development and production verification:

```bash
npm run dev      # start the development server
npm run build    # create the production bundle in dist/
npm run preview  # serve the built bundle locally
```

## Project structure

```text
src/
  audio/
    analyzer.js
    loader.js
  export/
    mp4Pipeline.js
    recorder.js
  render/
    preview.js
    stickman.js
  utils/
    math.js
  main.js
  style.css
public/
  favicon.svg
index.html
```
