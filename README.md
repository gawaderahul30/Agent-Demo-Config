# Lock-On Camera

A camera page that guides you while you aim. It shows one instruction at a time
(tilt, level, step back, lower the phone) and takes the photo when angle and position are right.

Open the published page in Chrome on an Android phone and tap **Start camera**.

## Shot types

| Shot | What it checks |
| --- | --- |
| Full body | Whole body in frame, phone at waist height, phone upright and level |
| Portrait | Head size in frame, phone at eye level, level (uses 2x zoom when the phone allows it) |
| Food 45° | Phone pointing 45° down, plate level |
| Top-down | Phone flat, directly above |
| Landscape | Horizon level, phone upright |

## How it works

- Tilt and level come from the phone's motion sensor (`deviceorientation`).
- Body position comes from MediaPipe Pose Landmarker, which runs on the phone.
- The camera's eye-level line is computed from the tilt reading. Whatever part of the body it
  crosses is at the same height as the phone, which is how "lower the phone" is decided.
- The picture is analysed on the device and is not uploaded. Photos stay in the page until you save or share them.

## Known limits

- Tested in desktop Chrome with a simulated camera and scripted sensor data, not yet on many real phones.
- Light is only checked for "too dark".
- The thresholds for distance and height are first values and may need tuning.

## Files

- `index.html` – the whole app.
- `vendor/tasks-vision/` – `@mediapipe/tasks-vision` 1.2.3 (Apache-2.0).
- `models/pose_landmarker_full.task` – MediaPipe Pose Landmarker (full) model (Apache-2.0).
