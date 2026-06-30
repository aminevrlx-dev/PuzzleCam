# PuzzleCam — Gesture Capture

A gesture-controlled photo booth app that runs entirely in the browser. No installation, no backend, no dependencies to install.

---

## **DESCRIPTION**

PuzzleCam captures a photo using your hands as a "frame", converts it into a 3x3 puzzle with a black-and-white photo booth effect, and lets you solve it using pinch gestures. Once completed, it saves to a downloadable photo strip.

---

## **SYSTEM REQUIREMENTS**

- **Browser:** Chrome or Edge (recommended), Firefox
- **Hardware:** Webcam
- **Internet connection:** Required to load the MediaPipe model (~10MB, first time only)
- **Local server:** Required to run the app (cannot be opened as a file directly)

---

## **INSTALLATION AND SETUP**

### 1. Clone the repository

```bash
git clone https://github.com/aminevrlx-dev/PuzzleCam.git
cd Puzzle
```

### 2. Start a local server

The app uses ES modules and camera access, so it needs to run over HTTP.

Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension in VS Code and click **Go Live**.

### 3. Open in the browser

```
http://localhost:5500
```

Allow camera access when prompted by the browser.

---

## **PROJECT STRUCTURE**

```
Puzzle/
├── index.html        # App entry point
├── app.js            # Full logic (tracking, puzzle, gallery)
├── css/
│   └── styles.css    # Styles and layout
└── .gitignore
```

---

## **CONTROL GESTURES**

| Gesture | Action |
|---|---|
| Both hands pinching | Freeze the area and start countdown |
| One hand pinching over a piece | Drag the puzzle piece |
| Closed fist (hold) | Save completed puzzle / Reset board |

---

## **APPLICATION LOGIC**

1. Show both hands to the camera and pinch to define the capture frame
2. Hold the pinch during the countdown — the photo is taken automatically
3. The photo is split into a 3x3 puzzle with a black-and-white photo booth filter
4. Rearrange the pieces using pinch gestures
5. Once completed, close your fist to save to the strip with a fragmentation animation
6. Download the full strip when you have 3 puzzles saved

---

## **TECH STACK**

- **[MediaPipe Tasks Vision](https://developers.google.com/mediapipe)** `v0.10.14` — hand landmark detection
- **Canvas 2D API** — rendering, puzzle pieces, photo booth effect
- **JavaScript (ES Modules)** — no frameworks
- **CSS Custom Properties** — theming and layout

All external dependencies are loaded via CDN. No additional installation required.

---

## **TROUBLESHOOTING GUIDE**

### **Camera won't turn on**

Make sure no other application (Teams, Zoom, Discord, etc.) is using the camera in the background.

### **App fails to load the model**

Check your internet connection. The MediaPipe model (~10MB) is downloaded from `storage.googleapis.com` and the runtime from `cdn.jsdelivr.net`. If either of those domains is blocked on your network, the app will not be able to start.

### **App shows a black screen**

Make sure you are opening the app from a local server (HTTP), not directly as a file from the file explorer.

### **Pinch gesture is not detected**

Make sure you have good lighting and that both hands are visible to the camera. Bring your index finger and thumb closer together until the yellow dot on screen activates.

---

## **BROWSER COMPATIBILITY**

| Browser | Support |
|---|---|
| Chrome / Edge | Recommended |
| Firefox | Compatible |
| Safari | Limited (may require additional permissions) |
| Mobile | Limited (desktop recommended) |

---

## **LICENSE**

MIT — free to use, modify, and share.
