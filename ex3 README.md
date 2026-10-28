# Histogram Equalization Using OpenCV (Grayscale & Color Images)

---

## Aim

To write a Python program using OpenCV to perform histogram equalization on both grayscale and color images to enhance image contrast and brightness.

The program performs the following operations:

- Read and display a grayscale image  
- Plot histogram of the grayscale image  
- Apply histogram equalization on grayscale image  
- Read and display a color image  
- Plot histogram of B, G, R channels  
- Convert image to HSV color space  
- Apply histogram equalization on the Value (V) channel  
- Convert the enhanced image back to BGR format  
- Display original and enhanced images with histograms  

---

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

## Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the image `parrot.jpg` in grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display original grayscale image, its histogram, enhanced image, and its histogram using a 2 × 2 grid.

### Step 6:
Read the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display original color image, histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

---

## Program

### Developed By:
**Name:** ________MUTHU POORNIMA P____________________  

### Register No:
_________212224240099___________________  

import cv2
import numpy as np
import matplotlib.pyplot as plt
import os

# Step 6: Read the image in colour format
image_path = os.path.expanduser("~/Downloads/d2image.jpg")
img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    print("Image loaded successfully!")
    print("Image dimensions:", img.shape)

    # Convert BGR to RGB for displaying with Matplotlib
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Step 7: Split into B, G, R channels and plot histograms
    b, g, r = cv2.split(img)

    plt.figure(figsize=(12, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(img_rgb)
    plt.title("Original Colour Image")
    plt.axis("off")

    plt.subplot(2, 2, 2)
    plt.hist(b.ravel(), bins=256, range=[0, 256],
             color="blue", alpha=0.5, label="Blue")
    plt.hist(g.ravel(), bins=256, range=[0, 256],
             color="green", alpha=0.5, label="Green")
    plt.hist(r.ravel(), bins=256, range=[0, 256],
             color="red", alpha=0.5, label="Red")
    plt.title("B, G, R Channel Histograms")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Number of Pixels")
    plt.legend()

    # Step 8: Convert BGR to HSV
    hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
    h, s, v = cv2.split(hsv)

    # Step 9: Apply histogram equalization to V channel
    v_equalized = cv2.equalizeHist(v)

    # Step 10: Merge channels and convert back to BGR
    hsv_equalized = cv2.merge([h, s, v_equalized])
    enhanced_img = cv2.cvtColor(hsv_equalized, cv2.COLOR_HSV2BGR)
    enhanced_rgb = cv2.cvtColor(enhanced_img, cv2.COLOR_BGR2RGB)

    # Step 11: Display original, histogram, enhanced image and histogram
    plt.subplot(2, 2, 3)
    plt.imshow(enhanced_rgb)
    plt.title("Enhanced Image")
    plt.axis("off")

    plt.subplot(2, 2, 4)
    plt.hist(v.ravel(), bins=256, range=[0, 256],
             color="gray", alpha=0.5, label="Original V")
    plt.hist(v_equalized.ravel(), bins=256, range=[0, 256],
             color="orange", alpha=0.5, label="Equalized V")
    plt.title("V Channel Histogram Comparison")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Number of Pixels")
    plt.legend()

    plt.tight_layout()
    plt.show()

    # Save the enhanced image in Downloads
    output_path = os.path.expanduser("~/Downloads/dipt_enhanced.png")
    cv2.imwrite(output_path, enhanced_img)
    print("Enhanced image saved to:", output_path)
---

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast  

<img width="1325" height="525" alt="image" src="https://github.com/user-attachments/assets/f98aa599-e5f9-447c-a282-ece369fc9465" />



### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

<img width="1322" height="552" alt="image" src="https://github.com/user-attachments/assets/e8ac274c-43df-4fd2-a235-5d10b6ea3795" />

<img width="1341" height="530" alt="image" src="https://github.com/user-attachments/assets/f7513cf2-0532-4e5f-bb5b-6553b346c34f" />

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.

