# Image Segmentation Using Thresholding Techniques in OpenCV

## Aim

To segment an image using Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding techniques using Python and OpenCV.

The program performs the following operations:

- Global Thresholding
- Adaptive Thresholding
- Otsu's Thresholding

## Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Load the input image using OpenCV.

### Step 3:

Convert the input image into grayscale format.

### Step 4: Global Thresholding

- Select a fixed threshold value.
- Apply thresholding to separate foreground and background pixels.
- Display the thresholded image.

### Step 5: Adaptive Thresholding

- Compute threshold values for small regions of the image.
- Apply Adaptive Mean Thresholding.
- Apply Adaptive Gaussian Thresholding.
- Display the segmented images.

### Step 6: Otsu's Thresholding

- Automatically determine the optimal threshold value.
- Apply Otsu's thresholding technique.
- Display the segmented image.

### Step 7:

Compare the results obtained from Global, Adaptive, and Otsu's thresholding methods.

## Program
```

# Image Segmentation Using Thresholding Techniques

# Step 1: Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt
import os

# Step 2: Load the input image
image_path = os.path.expanduser("~/Downloads/8dipt.jpg")
img = cv2.imread(image_path)

if img is None:
    print("Error: Image not found! Check the filename and path.")

else:
    print("Image loaded successfully!")

    # Step 3: Convert image to grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 4: Global Thresholding
    ret, global_thresh = cv2.threshold(
        gray, 127, 255, cv2.THRESH_BINARY
    )

    # Step 5: Adaptive Mean Thresholding
    adaptive_mean = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_MEAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Adaptive Gaussian Thresholding
    adaptive_gaussian = cv2.adaptiveThreshold(
        gray, 255,
        cv2.ADAPTIVE_THRESH_GAUSSIAN_C,
        cv2.THRESH_BINARY,
        11, 2
    )

    # Step 6: Otsu's Thresholding
    otsu_value, otsu = cv2.threshold(
        gray, 0, 255,
        cv2.THRESH_BINARY + cv2.THRESH_OTSU
    )

    print("Global Threshold Value:", ret)
    print("Otsu Threshold Value:", otsu_value)

    # Step 7: Display all results for comparison
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 3, 1)
    plt.imshow(gray, cmap="gray")
    plt.title("Original Grayscale Image")
    plt.axis("off")

    plt.subplot(2, 3, 2)
    plt.imshow(global_thresh, cmap="gray")
    plt.title("Global Thresholding")
    plt.axis("off")

    plt.subplot(2, 3, 3)
    plt.imshow(adaptive_mean, cmap="gray")
    plt.title("Adaptive Mean Thresholding")
    plt.axis("off")

    plt.subplot(2, 3, 4)
    plt.imshow(adaptive_gaussian, cmap="gray")
    plt.title("Adaptive Gaussian Thresholding")
    plt.axis("off")

    plt.subplot(2, 3, 5)
    plt.imshow(otsu, cmap="gray")
    plt.title("Otsu's Thresholding")
    plt.axis("off")

    plt.tight_layout()
    plt.show()

    print("Image segmentation completed successfully!")
```
## Developed By

**Name:** _______MUTHU POORNIMA P_____________________

**Register No:** ___212224240099___________________

## Output

<img width="1328" height="567" alt="image" src="https://github.com/user-attachments/assets/a807e6ba-d615-4240-8b29-d0d83e25da3b" />

<img width="898" height="532" alt="image" src="https://github.com/user-attachments/assets/2f952b08-ea81-4383-8dc1-8b22d52c38a8" />

## Result

Thus, image segmentation is successfully performed using **Global Thresholding, Adaptive Thresholding, and Otsu's Thresholding** techniques in OpenCV. 
