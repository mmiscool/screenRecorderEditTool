# screencap.me — Screen Recorder + Editor

This repo contains a no-nonsense browser app for grabbing your screen + microphone, importing existing clips, dropping in title cards, trimming, and exporting one stitched video without touching FFmpeg or a backend.

![App screenshot showing capture preview, clip list, and export controls](./screenshot.png)

## Why use it
- Start capturing screen + mic instantly; every stop creates a new clip
- Import local video files to mix with recorded clips
- Add title blocks with editable text, font, color, alignment, duration, and optional background images (cover/contain)
- Trim start/end per clip with drag handles or numeric fields; reorder via drag or ↑/↓ controls
- Optional Webcam PiP so you can float your face cam while recording the screen
- Mic offset control (ms) to line up your audio with Webcam PiP if the camera feed lags
- Export the final video fully in-browser (canvas + MediaRecorder) as webm with a live render overlay + preview (and cancel)
- Save/load projects as a single JSON file (clips, title settings, and assets are embedded as base64)
- Zero installs or builds—just open `index.html` on `localhost`

## Quick start
1) Run a simple local server in the repo (screen capture needs a secure context):  
   `python -m http.server 8000` then open http://localhost:8000  
2) Click **Start Screen + Mic** and grant capture permissions; the preview turns live.  
3) Hit **Start Clip** to record; use the full-screen **Stop Recording** overlay to end. Repeat or bring in existing files with **Import Clip**.  
4) Want an intro/interstitial? Pick **Add Title Block** in the Clips panel, then edit text, font, color, duration, and background inline.  
5) Trim each clip with the handles/inputs under its thumbnail and reorder by dragging the index pill or using ↑/↓. Rename clips inline.  
6) Toggle **Webcam PiP** if you want a floating camera window; adjust **Mic offset (ms)** if the PiP feed lags behind audio.  
7) Click **Export Final Video**. Watch the render modal for progress/ETA and live preview; download the webm when the status reads “Done.”  

## Editing and workflow
- Clip list supports drag-and-drop or ↑/↓ reordering, inline titles, and delete × controls.
- Video clips include play/pause on thumbnail tap, a trim overlay with handles, and numeric start/end fields that update the playhead.
- Title blocks render a live preview and expose controls for font, size, color, alignment, duration, and background image fit.
- Export runs fully in-browser; the render modal shows progress, ETA, and a live preview (with a cancel option).
- Use **Mic offset (ms)** to delay mic audio when Webcam PiP is active; changes apply when capture is idle.

## Project files
- **Export Project** writes a JSON that embeds all clips, trims, and title block backgrounds/fonts/text so nothing leaves the browser.  
- **Import Project** reloads that JSON and restores clips, trims, order, and title styling.  
- Downloads stay in your browser—no server round-trips.

## Notes
- Works in modern Chromium-based browsers; screen capture may require selecting a tab/window and enabling audio.
- Everything stays local; close the tab or refresh to clear captures unless you export the project or final video.
