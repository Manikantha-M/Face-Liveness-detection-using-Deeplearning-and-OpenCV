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
 Obtained from video of myself.
 <p align="center">
   <img src="cap1.JPG">
  </p>
  
## sample dataset  for fake(pic,video)
Video shooted while the orignal video playing on my laptop screen.
 <p align="center">
   <img src="Cap2.JPG">
  </p>
  
  # Theory
  In order to create the liveness detector, I’ll be training a deep neural network capable of distinguishing between real versus fake faces

1.Build the image dataset itself.

2.Implement a CNN capable of performing liveness detector.

3.Train the liveness detector network.

4.Create a Python + OpenCV script capable of taking our trained liveness detector model and apply it to real-time video.

I'll be treating liveness detection as a binary classification problem.

Given an input image, I’ll train a Convolutional Neural Network capable of distinguishing real faces from fake faces.

In order to build the liveness detection dataset:

I Took my Phone and put it in selfie mode. Recorded a ~12-second video of myself.
Replayed the same 12-second video, this time facing my Phone towards my laptop where I recorded the video replaying.
This resulted in two example videos, one for “real” faces and another for “fake” faces.
Finally, I applied face detection to both sets of videos to extract individual face ROIs for both classes.
## Python scripts description
### gather_examples.py :
This script grabs face ROIs from input video files, and generates the required dataset.
Real = 148 and Fake = 121;  Total = 269 faces.
### livenessnet.py
The next step is to implement “LivenessNet”, the deep learning-based liveness detector.
<p align="center">
   <img src="videos/img2.png">
  </p>

### train_liveness.py
This consists all the code required for training.
### liveness_demo.py
Access the webcam stream and apply face detection to each frame. For each face detected, apply the liveness detector model.

## model summary

model.summary()

Model: "sequential_8"
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
conv2d_13 (Conv2D)           (None, 32, 32, 16)        448       
_________________________________________________________________
activation_12 (Activation)   (None, 32, 32, 16)        0         
_________________________________________________________________
batch_normalization_11 (Batc (None, 32, 32, 16)        64        
_________________________________________________________________
conv2d_14 (Conv2D)           (None, 32, 32, 16)        2320      
_________________________________________________________________
activation_13 (Activation)   (None, 32, 32, 16)        0         
_________________________________________________________________
batch_normalization_12 (Batc (None, 32, 32, 16)        64        
_________________________________________________________________
max_pooling2d_5 (MaxPooling2 (None, 16, 16, 16)        0         
_________________________________________________________________
dropout_7 (Dropout)          (None, 16, 16, 16)        0         
_________________________________________________________________
conv2d_15 (Conv2D)           (None, 16, 16, 32)        4640      
_________________________________________________________________
activation_14 (Activation)   (None, 16, 16, 32)        0         
_________________________________________________________________
batch_normalization_13 (Batc (None, 16, 16, 32)        128       
_________________________________________________________________
conv2d_16 (Conv2D)           (None, 16, 16, 32)        9248      
_________________________________________________________________
activation_15 (Activation)   (None, 16, 16, 32)        0         
_________________________________________________________________
batch_normalization_14 (Batc (None, 16, 16, 32)        128       
_________________________________________________________________
max_pooling2d_6 (MaxPooling2 (None, 8, 8, 32)          0         
_________________________________________________________________
dropout_8 (Dropout)          (None, 8, 8, 32)          0         
_________________________________________________________________
flatten_3 (Flatten)          (None, 2048)              0         
_________________________________________________________________
dense_3 (Dense)              (None, 64)                131136    
_________________________________________________________________
activation_16 (Activation)   (None, 64)                0         
_________________________________________________________________
batch_normalization_15 (Batc (None, 64)                256       
_________________________________________________________________
dropout_9 (Dropout)          (None, 64)                0         
_________________________________________________________________
dense_4 (Dense)              (None, 2)                 130       
_________________________________________________________________
activation_17 (Activation)   (None, 2)                 0         
=================================================================
Total params: 148,562
Trainable params: 148,242
Non-trainable params: 320
_________________________________________________________________
