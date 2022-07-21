# Object Detection

Object detection helps robots and computers naviagte through obstacles in their way. Without object detection modern day robots would not be able to take a step forward.

| **Name** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Shuchir. | Evergreen Valley Highschool | Electrical Engineering | Incoming Senior

![39ca83c1-0a4f-41eb-80cb-15f0fceede85](https://user-images.githubusercontent.com/62129061/180271338-93fff5fe-fefc-4372-8323-d499138de607.jpg)


<p align="center">
  <img src="https://raw.githubusercontent.com/suchturbo/Object-detection-code/main/branding/BlueStamp-Engineering-Logo-White.png" />
</p>

 
# Project

Here is a picture of my project and a small sample of what it does

![Screenshot (50)](https://user-images.githubusercontent.com/62129061/180272585-26df6a8e-561b-42c4-b530-23d0b8fadc6b.png)



# Final Milestone
My final milestone is the increased reliability and accuracy of my robot. But, unfortunately in the middle of developing my final project my rasberry pi stopped working. I had to waste 3 days trying to find a new rasberry pi and finally when I got it it took more time trying to set it up again. Fortunately, I got it working using the old code I had on my broken rasberry pi and I finished my main project. I increased the accuracy and even added more objects that it could detect like the chair.  Hopefully one day I wil be able to use the knowledge I gained from this programming in the real world. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/k7kFMKFyNmw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
# First Milestone

My first milestone came with setting up the actual rasberry pi and all the neccessary components to my monitor. I started off by adding the SD card in and connecting the HDMI cable for my monitor into the rasberry pi. Then I added in the raspi cameras and connected my rasberry pi into VNC which would allow me to stream everything that went on in my rasberry pi into my local computer. I first updated my rasberry pi thourougly in order to run my raspi camera. To my surprise my raspi camera did not work and even the second one after that did not work either. After all this I just used my personal webcam and hooked it up into my rasberry pi. I downloaded models which my code would scan for. After I ran a couple of models I ended with approximately 70% accuracy. With my webcam working I decided to move onto the next step.

 <iframe width="560" height="315" src="https://www.youtube.com/embed/0dlQdvDuWSg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Code for webcam activation
```python
import cv2
import numpy as mp
import time
from threading import Thread

class VideoStream:
    """Camera object that controls video streaming"""
    def __init__(self,resolution=(640,480),framerate=30):
        # Initialize the PiCamera and the camera image stream
        self.stream = cv2.VideoCapture(0)
        ret = self.stream.set(cv2.CAP_PROP_FOURCC, cv2.VideoWriter_fourcc(*'MJPG'))
        ret = self.stream.set(3,resolution[0])
        ret = self.stream.set(4,resolution[1])
            
        # Read first frame from the stream
        (self.grabbed, self.frame) = self.stream.read()

    # Variable to control when the camera is stopped
        self.stopped = False

    def start(self):
    # Start the thread that reads frames from the video stream
        Thread(target=self.update,args=()).start()
        return self

    def update(self):
        # Keep looping indefinitely until the thread is stopped
        while True:
            # If the camera is stopped, stop the thread
            if self.stopped:
                # Close camera resources
                self.stream.release()
                return

            # Otherwise, grab the next frame from the stream
            (self.grabbed, self.frame) = self.stream.read()

    def read(self):
    # Return the most recent frame
        return self.frame

    def stop(self):
    # Indicate that the camera and thread should be stopped
        self.stopped = True
        
imW, imH = 1280, 720
videostream = VideoStream(resolution = (imW, imH), framerate = 30).start()
time.sleep(1)
while True:
    frame = videostream.read()
    framergb = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
    frame1 = frame.copy()
    cv2.imshow('test', frame1)
    cv2.waitKey(1)
```
