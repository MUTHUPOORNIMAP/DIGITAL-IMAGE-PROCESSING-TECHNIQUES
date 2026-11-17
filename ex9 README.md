# Implementation of Erosion and Dilation Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological operations such as Erosion and Dilation on an image.

The program performs the following operations:

- Image Erosion
- Image Dilation

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

Create a blank image using NumPy.

### Step 3:

Insert text onto the image using OpenCV's text drawing function.

### Step 4:

Display the original image.

### Step 5:

Create a structuring element (kernel) of suitable size.

### Step 6: Image Erosion

- Apply the erosion operation using the created kernel.
- Remove pixels from the boundaries of foreground objects.
- Display the eroded image.

### Step 7: Image Dilation

- Apply the dilation operation using the same kernel.
- Add pixels to the boundaries of foreground objects.
- Display the dilated image.

### Step 8:

Compare the original, eroded, and dilated images.

## Program
```
# Step 1: Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Step 2: Create a blank image
img = np.zeros((300, 500), dtype=np.uint8)

# Step 3: Insert text into the image
cv2.putText(img, "POORNIMA",
            (30, 160),
            cv2.FONT_HERSHEY_SIMPLEX,
            1.2, 255, 3)

# Step 4: Display original image
plt.figure(figsize=(12, 4))

plt.subplot(1, 3, 1)
plt.imshow(img, cmap="gray")
plt.title("Original Image")
plt.axis("off")

# Step 5: Create structuring element (kernel)
kernel = np.ones((5, 5), np.uint8)

# Step 6: Apply Erosion
erosion = cv2.erode(img, kernel, iterations=1)

plt.subplot(1, 3, 2)
plt.imshow(erosion, cmap="gray")
plt.title("Eroded Image")
plt.axis("off")

# Step 7: Apply Dilation
dilation = cv2.dilate(img, kernel, iterations=1)

plt.subplot(1, 3, 3)
plt.imshow(dilation, cmap="gray")
plt.title("Dilated Image")
plt.axis("off")

# Step 8: Display all images
plt.tight_layout()
plt.show()

print("Erosion and Dilation completed successfully!")
```
## Developed By

**Name:** ___MUTHU POORNIMA P_________________________

**Register No:** ______212224240099________________

## Output

<img width="1380" height="350" alt="image" src="https://github.com/user-attachments/assets/a510be71-48e2-44fb-b8c3-ac5017aeb7f6" />


### Original Image

- A text image containing characters is displayed.
- The image serves as the input for morphological processing.

### Erosion

- Original image is displayed.
- Eroded image is displayed.
- The thickness of the characters is reduced.
- Object boundaries shrink inward.

### Dilation

- Original image is displayed.
- Dilated image is displayed.
- The thickness of the characters increases.
- Object boundaries expand outward.

## Result

Thus, the morphological operations **Erosion** and **Dilation** are successfully implemented using OpenCV.
