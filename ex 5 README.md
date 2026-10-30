# Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** ___MUTHU POORNIMA P_________________________  
- **Register No:** __________212224240099____________
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
import os

# Step 1 and 2: Import libraries and read the input image
image_path = os.path.expanduser("~/Downloads/image1.jpg")
img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load d2image.jpg. Check the file path.")
else:
    # Step 3: Convert BGR to RGB for display
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Step 4: Apply Averaging Filter
    averaging = cv2.blur(img, (5, 5))

    # Step 5: Apply Weighted Averaging Filter
    kernel = np.array([
        [1, 2, 1],
        [2, 4, 2],
        [1, 2, 1]
    ], dtype=np.float32) / 16

    weighted = cv2.filter2D(img, -1, kernel)

    # Step 6: Apply Gaussian Filter
    gaussian = cv2.GaussianBlur(img, (5, 5), 0)

    # Step 7: Apply Median Filter
    median = cv2.medianBlur(img, 5)

    # Step 8: Apply Laplacian Sharpening using a kernel
    laplacian_kernel = np.array([
        [0, -1, 0],
        [-1, 5, -1],
        [0, -1, 0]
    ], dtype=np.float32)

    sharpened = cv2.filter2D(img, -1, laplacian_kernel)

    # Step 9: Convert to grayscale and apply Laplacian operator
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian_abs = cv2.convertScaleAbs(laplacian)

    # Convert filtered images from BGR to RGB
    averaging_rgb = cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB)
    weighted_rgb = cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB)
    gaussian_rgb = cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB)
    median_rgb = cv2.cvtColor(median, cv2.COLOR_BGR2RGB)
    sharpened_rgb = cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB)

    # Step 10: Display all images for comparison
    plt.figure(figsize=(15, 12))

    plt.subplot(3, 3, 1)
    plt.imshow(img_rgb)
    plt.title("Original Image")
    plt.axis("off")

    plt.subplot(3, 3, 2)
    plt.imshow(averaging_rgb)
    plt.title("Averaging Filter")
    plt.axis("off")

    plt.subplot(3, 3, 3)
    plt.imshow(weighted_rgb)
    plt.title("Weighted Averaging Filter")
    plt.axis("off")

    plt.subplot(3, 3, 4)
    plt.imshow(gaussian_rgb)
    plt.title("Gaussian Filter")
    plt.axis("off")

    plt.subplot(3, 3, 5)
    plt.imshow(median_rgb)
    plt.title("Median Filter")
    plt.axis("off")

    plt.subplot(3, 3, 6)
    plt.imshow(sharpened_rgb)
    plt.title("Laplacian Sharpening")
    plt.axis("off")

    plt.subplot(3, 3, 7)
    plt.imshow(gray, cmap="gray")
    plt.title("Grayscale Image")
    plt.axis("off")

    plt.subplot(3, 3, 8)
    plt.imshow(laplacian_abs, cmap="gray")
    plt.title("Laplacian Operator")
    plt.axis("off")

    plt.tight_layout()
    plt.show()

    print("All image filters applied successfully!")
```
---

##  Output

### Smoothing Filters


<img width="1421" height="485" alt="image" src="https://github.com/user-attachments/assets/b4abc829-1507-4d6b-b93c-b41ef1da9aa0" />

<img width="1370" height="470" alt="image" src="https://github.com/user-attachments/assets/9c534653-8f82-496b-ab36-01be3e93a7e2" />

<img width="837" height="503" alt="image" src="https://github.com/user-attachments/assets/2386a93d-a351-4064-bf93-d85706bf2fdf" />



---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
