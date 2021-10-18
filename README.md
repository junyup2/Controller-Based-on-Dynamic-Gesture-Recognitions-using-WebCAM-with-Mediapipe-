
---
# Controller-Based-on-Dynamic-Gesture-Recognitions-using-WebCAM-with-Mediapipe

Estimate hand pose using MediaPipe(Python version).<br> 
This is a program that recognizes hand signs and hand gestures with a simple MLP using the detected key points for control windows.

This repository contains the following contents.
* Windows Control(Mouse) program
    - HandGestureWindowsControl.py
* Hand sign recognition model(TFLite) - Static
* Hand gesture recognition model(TFLite) - Dynamic
* Learning data for hand sign recognition and notebook for learning
* Learning data for hand gesture recognition and notebook for learning

# Requirements
* python 3.8.10
* mediapipe 0.8.1
* OpenCV 4.5.2 or Later
* Tensorflow 2.6.0 or Later
* autopy 4.0.0

# Demo
You can Control Mouse using your webcam in Windows 10.
```bash
HandGestureWindowsControl.py
```

The following options can be specified when running the demo.
* --device<br>Specifying the camera device number (Default：0)
* --width<br>Width of camera captured image (Default：960)
* --height<br>Height of camera captured image (Default：540)
* --use_static_image_mode<br>Whether to use static_image_mode option for MediaPipe inference (Default：Unspecified)
* --min_detection_confidence<br>
Detection confidence threshold (Default：0.8)
* --min_tracking_confidence<br>
Tracking confidence threshold (Default：0.5)

# Directory
<pre>
│  HandGestureWindowsControl.py
│  keypoint_classification.ipynb
│  point_history_classification.ipynb
│  
├─model
│  ├─keypoint_classifier
│  │  │  keypoint.csv
│  │  │  keypoint_classifier.hdf5
│  │  │  keypoint_classifier.py
│  │  │  keypoint_classifier.tflite
│  │  └─ keypoint_classifier_label.csv
│  │          
│  └─point_history_classifier
│      │  point_history.csv
│      │  point_history_classifier.hdf5
│      │  point_history_classifier.py
│      │  point_history_classifier.tflite
│      └─ point_history_classifier_label.csv
│          
└─utils
    └─cvfpscalc.py
</pre>

### HandGestureWindowsControl.py
This is a sample program for inference.<br>
In addition, learning data (key points) for hand sign recognition,<br>
You can also collect training data (index finger coordinate history) for finger gesture recognition.

### keypoint_classification.ipynb
This is a model training script for hand sign recognition.

### point_history_classification.ipynb
This is a model training script for hand gesture recognition.

### model/keypoint_classifier
This directory stores files related to hand sign recognition.<br>
The following files are stored.
* Training data(keypoint.csv)
* Trained model(keypoint_classifier.tflite)
* Label data(keypoint_classifier_label.csv)
* Inference module(keypoint_classifier.py)

### model/point_history_classifier
This directory stores files related to hand gesture recognition.<br>
The following files are stored.
* Training data(point_history.csv)
* Trained model(point_history_classifier.tflite)
* Label data(point_history_classifier_label.csv)
* Inference module(point_history_classifier.py)

### utils/cvfpscalc.py
This is a module for FPS measurement.

# Training
Hand sign recognition and hand gesture recognition can add and change training data and retrain the model.

The key point coordinates
<img src="https://user-images.githubusercontent.com/37477845/102242918-ed328c80-3f3d-11eb-907c-61ba05678d54.png" width="80%">

# Control

## Hand Sign
* `hand sign` limits the `hand gesture`
    - Certain hand gestures operate only under certain hand signs.

## Hand Gesture
* None
* Wheel Up
* Wheel Down
* Click
* Drag

# Reference
* [MediaPipe](https://mediapipe.dev/)
* [Kazuhito00/hand-gesture-recognition-using-mediapipe](https://github.com/Kazuhito00/hand-gesture-recognition-using-mediapipe)

# License 
Controller-Based-on-Dynamic-Gesture-Recognitions-using-WebCAM-with-Mediapipe is under [Apache v2 license](LICENSE).