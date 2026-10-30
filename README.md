# Object Detecting Camera

Real-time object detection on a Raspberry Pi, built during the BlueStamp Engineering summer program.

**Project write-up, milestones, and code: [suchturbo.github.io/Object-detection-code](https://suchturbo.github.io/Object-detection-code/)**

## What it does

A Raspberry Pi reads frames from a USB webcam and runs a pre-trained detection model on each frame, drawing labeled boxes around objects it recognizes. The goal was a camera a robot could use to see and avoid obstacles.

## Built with

- Raspberry Pi with a USB webcam
- Python, OpenCV, NumPy
- A threaded video stream class so frame capture never blocks detection
- VNC to view the Pi's desktop remotely

## Milestones

1. Set up the Pi and its peripherals. The Pi camera modules failed, so I switched to a USB webcam and evaluated several detection models.
2. The Pi itself failed midway through the project. I set up a replacement, restored the code, improved detection accuracy, and added more object classes such as chairs.

The full write-up lives on the `gh-pages` branch and is published at the link above.
