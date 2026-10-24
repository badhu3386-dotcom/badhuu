# Sign to Voice

A website that reads sign language through your laptop webcam, shows the result as text on screen, and speaks it aloud.

- **Hand tracking:** [MediaPipe Hands](https://developers.google.com/mediapipe/solutions/vision/hand_landmarker) finds 21 landmark points on your hand.
- **Recognition:** a small k-Nearest-Neighbours classifier compares your hand pose against signs you have taught it.
- **Voice:** the browser's built-in Web Speech API (English, Hindi, Malayalam, Tamil, and more, depending on the voices installed on your device).
- **Privacy:** everything runs in the browser. No video leaves your computer.

## How to use

1. Click **Start camera** and allow access.
2. Under **Teach a sign**, type a word (e.g. `Hello`), make the sign, press **Record**. Repeat 2-3 times with small variations. Add as many signs as you like.
3. Make a sign and hold it steadily. The word appears in **Translation** and is spoken.
4. Use **Export signs** to back up your data, and **Import signs** to load it on another device.

Start with 5-10 signs. Once those work well, add more.

## Run locally

The camera only works on `https` or `localhost`, so don't just double-click `index.html`. From this folder:

```bash
python -m http.server 8000
```

Then open <http://localhost:8000> in Chrome or Edge.

## Put it online with GitHub Pages

1. Create a new GitHub repository and upload all files from this folder.
2. Go to **Settings -> Pages**, set the source to the `main` branch and root folder, and save.
3. After a minute your site is live at `https://<your-username>.github.io/<repo-name>/` (https, so the camera works).

## Project files

| File | Purpose |
|------|---------|
| `index.html` | Page layout |
| `style.css` | Styling |
| `app.js` | Camera, hand tracking, classifier, speech |

## Tips for better accuracy

- Good, even lighting and a plain background.
- Record each sign several times, at slightly different distances and angles.
- Make signs look clearly different from each other.
- Adjust **Hold time** and **Strictness** sliders in the Translation panel.

## Limitations and next steps

- Tracks **one hand** and recognises **static poses** (letters, numbers, simple words). Signs that depend on movement, or on two hands, need more work.
- Ideas: two-hand support, motion signs using sequences of frames (LSTM), a pre-trained ISL dataset, sentence building.
