# Count-number-of-Faces-in-video-using-Python-OpenCV

markdown
# Face Detection with Python and OpenCV

This project demonstrates how to count the number of faces in an image or a video stream using Python and OpenCV.

## Table of Contents
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Usage](#usage)
 

## Requirements
- Python 3.x
- OpenCV (cv2)

You can install OpenCV using pip:

pip install opencv-python


## Getting Started
1. Clone this repository or download the code files.

2. If you're working with an image, place your image file in the project directory.

3. If you're working with a video, place your video file in the project directory.

## Usage
### For Image:
bash
python face_detection_image.py

Replace 'your_image.jpg' in `face_detection_image.py` with your image file's name.

### For Video:
bash
python face_detection_video.py

Replace 'your_video.mp4' in `face_detection_video.py` with your video file's name.

 import cv2
from google.colab.patches import cv2_imshow
# Load the cascade classifier for face detection
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

# Open a video capture
cap = cv2.VideoCapture('/content/video.mp4')  # Replace 'your_video.mp4' with the path to your video file

while True:
    ret, frame = cap.read()

    if not ret:
        break

    # Detect faces in the frame
    faces = face_cascade.detectMultiScale(frame, scaleFactor=1.1, minNeighbors=5, minSize=(30, 30))

    # Get the number of faces found
    num_faces = len(faces)

    # Draw rectangles around the faces
    for (x, y, w, h) in faces:
        cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)

    # Display the frame with faces
    cv2_imshow(frame)

    # Exit the loop when 'q' is pressed
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# Release the video capture and close all OpenCV windows
cap.release()
cv2.destroyAllWindows()

# Print the number of faces found
print("Number of faces detected: " + str(num_faces))
![image](https://github.com/surajmhulke/Count-number-of-Faces-in-video-using-Python-OpenCV/assets/136318267/e3a9b625-8911-43c0-9057-3da61e19e873)

print("Number of faces detected: " + str(num_faces))

Number of faces detected: 1
