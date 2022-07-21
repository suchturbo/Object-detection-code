Object Detection

Object detection helps robots and computers naviagte through obstacles in their way. Without object detection modern day robots would not be able to take a step forward.

| **Name** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Shuchir. | Evergreen Valley Highschool | Electrical Engineering | Incoming Senior



![Headstone Image](https://github.com/BlueStampEng/BSE_Template_Portfolio/blob/4655d8c4b2f1d0fa5912511d0b39542520b9f88e/branding/BlueStamp-Engineering-Logo-White.png)
  
# Final Milestone
My final milestone is the increased reliability and accuracy of my robot. I ameliorated the sagging and fixed the reliability of the finger. As discussed in my second milestone, the arm sags because of weight. I put in a block of wood at the base to hold up the upper arm; this has reverberating positive effects throughout the arm. I also realized that the forearm was getting disconnected from the elbow servo’s horn because of the weight stress on the joint. Now, I make sure to constantly tighten the screws at that joint. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/k7kFMKFyNmw" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  
# First Milestone

My first milestone came with setting up the actual rasberry pi and all the neccessary components to my monitor. I started off by adding the SD card in and connecting the HDMI cable for my monitor into the rasberry pi. Then I added in the raspi cameras and connected my rasberry pi into VNC which would allow me to stream everything that went on in my rasberry pi into my local computer. I first updated my rasberry pi thourougly in order to run my raspi camera. To my surprise my raspi camera did not work and even the second one after that did not work either. After all this I just used my personal webcam and hooked it up into my rasberry pi. I downloaded models which my code would scan for. After I ran a couple of models I ended with approximately 70% accuracy. With my webcam working I decided to move onto the next step.

 <iframe width="560" height="315" src="https://www.youtube.com/embed/0dlQdvDuWSg" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

# Code for webcam activation

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

