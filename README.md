# TG hackathon 2
## training the liveness detection model
 <p align="center">
   <img src="train1.JPG">
  </p>

 <p align="center">
   <img src="train2.JPG">
  </p>

# Outputs of webcam stream - real(liveness) vs fake(pic,video)
## output1
 <p align="center">
   <img src="output1.gif">
  </p>
  
## output2
 <p align="center">
   <img src="output2.gif">
  </p>
  
 ## sample dataset for real(liveness)
 <p align="center">
   <img src="cap1.JPG">
  </p>
  
## sample dataset  for fake(pic,video)
 <p align="center">
   <img src="Cap2.JPG">
  </p>
  
  # Theory
  In order to create the liveness detector, I’ll be training a deep neural network capable of distinguishing between real versus fake faces
1.Build the image dataset itself.

2.Implement a CNN capable of performing liveness detector.

3.Train the liveness detector network.

4.Create a Python + OpenCV script capable of taking our trained liveness detector model and apply it to real-time video.
