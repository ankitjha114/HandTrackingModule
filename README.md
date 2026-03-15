# HandTrackingModule

**Project Overview**


This project implements a real-time hand tracking module using Python, OpenCV, and MediaPipe. The system detects hands from a webcam feed and tracks 21 hand landmarks provided by MediaPipe. These landmarks allow us to determine the position of each finger joint and build gesture-based applications.

The module processes frames captured from a webcam, detects hands using MediaPipe's deep learning model, and visualizes the hand skeleton by drawing landmark connections. Additionally, it extracts coordinates of each landmark so they can be used for gesture recognition, virtual controls, or human–computer interaction applications.

This module serves as a foundation for advanced computer vision projects such as:

Virtual mouse control

Gesture recognition systems

Sign language recognition

AR/VR interaction

AI desktop assistants

**Technologies and Libraries Used**
1️ Python

Python is used as the main programming language because of its simplicity and strong ecosystem for machine learning and computer vision.

2️ OpenCV (cv2)

OpenCV is used for:

Accessing the webcam

Capturing video frames

Displaying images

Drawing shapes and text on frames

Example usage:

Capturing video frames

Displaying processed images

Drawing circles and text overlays

3️ MediaPipe

MediaPipe is a powerful framework developed by Google for building multimodal machine learning pipelines.

The MediaPipe Hands model detects:

Palm position

21 hand landmarks

Finger joint locations

Hand skeleton connections

This allows accurate real-time hand tracking with very low latency.

4️ Time Library

The time module is used to calculate FPS (Frames Per Second) so that we can monitor the performance of the real-time system.


**How the System Works (Step-by-Step)**

Step 1 — Capture Webcam Video

The webcam feed is captured using OpenCV.

cap = cv2.VideoCapture(0)

Each frame is read continuously from the webcam.

Step 2 — Convert Image Color Format

MediaPipe requires images in RGB format, while OpenCV uses BGR.

Therefore the frame is converted:

imgRGB = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
Step 3 — Hand Detection using MediaPipe

The MediaPipe Hands model processes the frame and detects hands.

self.results = self.hands.process(imgRGB)

If hands are detected, MediaPipe returns landmark data.

Step 4 — Draw Hand Landmarks

Each detected hand contains 21 landmarks.

These landmarks are drawn using MediaPipe's drawing utilities:

self.mpDraw.draw_landmarks(img, handLms, self.mpHands.HAND_CONNECTIONS)

This creates the visible hand skeleton.

Step 5 — Extract Landmark Coordinates

Each landmark contains normalized coordinates (x, y).

They are converted to pixel positions:

cx = int(lm.x * w)
cy = int(lm.y * h)

**These coordinates allow further analysis such as:**


Finger detection

Gesture recognition

Distance calculations

Step 6 — Calculate FPS

FPS is calculated using time differences between frames:

fps = 1/(cTime - pTime)

This helps monitor performance of the system.

 How to Set Up the Project in VS Code
Step 1 — Install Python

Download Python from:

https://python.org


**Check installation:**

python --version
Step 2 — Install VS Code

Download Visual Studio Code:

https://code.visualstudio.com

Install the Python Extension from Microsoft.

Step 3 — Create Project Folder

Example:

HandTrackingProject

Open this folder in VS Code.

Step 4 — Create a Virtual Environment

Creating a virtual environment isolates project dependencies.

Run in terminal:

python -m venv myenv
Step 5 — Activate Virtual Environment
Windows
myenv\Scripts\activate
Mac/Linux
source myenv/bin/activate

After activation, the terminal will show:

(myenv)
Step 6 — Install Required Libraries


**Install OpenCV and MediaPipe:**


pip install opencv-python
pip install mediapipe

You can verify installation:

pip list
Step 7 — Run the Program

Execute the Python script:

python HandTrackingModule.py

The webcam window will open and start tracking hands in real time.

Press Q to exit the program.


**Output**

The program will:

Detect hands in real time

Display hand landmarks

Show skeleton connections

Print landmark coordinates

Display FPS on screen


**Future Improvements**

This module can be extended to build advanced projects such as:

Gesture-controlled volume system

Virtual mouse using hand gestures

AI-based sign language translator

AR/VR hand interaction

Touchless UI systems


**References**


MediaPipe Documentation
https://developers.google.com/mediapipe

OpenCV Documentation
https://opencv.org


 **Author**


Ankit Kumar Jha

Computer Vision & AI Enthusiast
Focused on building creative machine learning and computer vision projects.
