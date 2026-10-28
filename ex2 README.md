# Image Capture and Video Processing Using OpenCV

---

## Aim

To write a Python program using OpenCV to capture an image from the webcam and perform the following operations:

1. Write the frame as a JPG file  
2. Display the video  
3. Display the video by resizing the window  
4. Rotate and display the video  

---

## 🛠️ Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  

---

## ⚙️ Algorithm

### Step 1:
Import the required libraries and initialize the webcam using `cv2.VideoCapture()`.

### Step 2:
Capture frames continuously from the webcam.

### Step 3:
Save a frame as a JPG image using `cv2.imwrite()`.

### Step 4:
Display the live video stream using `cv2.imshow()`.

### Step 5:
Resize the frame and rotate it using OpenCV functions, then display the processed frames.

---

## 💻 Program

### Developed By:
**Name:** __________Muthu Poornima __________________  

### Register No:
______________212224240099______________  

import cv2
import os

# Step 1: Initialize webcam
cap = cv2.VideoCapture(0)

if not cap.isOpened():
    print("Error: Cannot open webcam.")
else:
    print("Webcam started!")
    print("Press S to capture a photo.")
    print("Press Q to quit.")

    save_path = os.path.expanduser("~/Downloads/exp2image.jpg")

    # Step 2: Capture frames continuously
    while True:
        ret, frame = cap.read()

        if not ret:
            print("Cannot capture frame.")
            break

        # Step 5: Resize and rotate the frame
        resized = cv2.resize(frame, (640, 480))
        rotated = cv2.rotate(
            resized, cv2.ROTATE_90_CLOCKWISE
        )

        # Step 4: Display live video
        cv2.imshow("Live Webcam", frame)
        cv2.imshow("Resized and Rotated", rotated)

        # Step 3: Save a photo when S is pressed
        key = cv2.waitKey(1) & 0xFF

        if key == ord('s'):
            cv2.imwrite(save_path, frame)
            print("Photo saved:", save_path)

        elif key == ord('q'):
            break

    # Release resources
    cap.release()
    cv2.destroyAllWindows()
    print("Experiment completed.")
---

## Output

### i) Write the frame as JPG image
Captured image is saved as `captured_image.jpg`

<img width="801" height="641" alt="image" src="https://github.com/user-attachments/assets/626bafc9-9515-4bbe-8137-667ca1388377" />

### ii) Display the video
Live webcam video is displayed

<img width="801" height="641" alt="image" src="https://github.com/user-attachments/assets/e28cf8e2-e8c1-4c40-b007-a0afa308853d" />


### iii) Display the video by resizing the window
Video is shown in resized resolution (640 × 480)

### iv) Rotate and display the video
Video is displayed after rotation (90° clockwise)

<img width="600" height="827" alt="image" src="https://github.com/user-attachments/assets/986f1c20-424f-4405-b65c-1b6983fe1603" />

---

## Result

Thus, the image is successfully captured from the webcam and various video processing operations such as saving, displaying, resizing, and rotating are performed using OpenCV.

