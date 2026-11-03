#  Lane Detection

##  Aim

To implement a basic lane detection pipeline using OpenCV by completing missing code segments at specified locations.

---

## Learning Objective

* Understand each stage of image processing
* Learn how to build a complete computer vision pipeline
* Practice writing code in guided sections

**Important Instruction:**
👉 Write code **ONLY in places marked as `# Your Code Here`**
👉 Do NOT modify any other part of the code

---

##  Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

---

##  Algorithm & Explanation

---

###  Step 1: Import Libraries

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

---

###  Step 2: Read the Image

```python
# Read the image using OpenCV

###
image = cv2.imread(r'C:\Users\admin\Downloads\exp7image.jpg')
image = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)
###
```

---

###  Step 3: Convert to Grayscale

```python
# Convert to grayscale.

###
gray = cv2.cvtColor(image, cv2.COLOR_RGB2GRAY)
###
```

---

###  Step 4: Display Images

```python
plt.figure(figsize=(10,5))

###
plt.figure(figsize=(10,5))
plt.subplot(1,2,1)
plt.imshow(image)
plt.title('Original Image')
plt.axis('off')

plt.subplot(1,2,2)
plt.imshow(gray, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
plt.show()
###
```

---

###  Step 5: Thresholding

```python
# Apply thresholding

threshold = 
###
threshold = cv2.threshold(gray, 150, 255, cv2.THRESH_BINARY)[1]

plt.imshow(threshold, cmap='gray')
plt.title('Thresholded Image')
plt.axis('off')
plt.show()
###
```

---

###  Step 6: Region of Interest (ROI)

```python
# ROI masking already provided
# (Do not modify)
height, width = gray.shape

mask = np.zeros_like(gray)

polygon = np.array([[
    (0, height),
    (width, height),
    (width, int(height * 0.6)),
    (0, int(height * 0.6))
]])

cv2.fillPoly(mask, polygon, 255)
roi = cv2.bitwise_and(threshold, mask)

plt.imshow(roi, cmap='gray')
plt.title('ROI Masked Image')
plt.axis('off')
plt.show()
```

---

### Step 7: Edge Detection (Canny)

```python
# Perform Edge Detection

###
edges = cv2.Canny(roi, 50, 150)

plt.imshow(edges, cmap='gray')
plt.title('Edge Detection')
plt.axis('off')
plt.show()
###
```

---

###  Step 8: Gaussian Blur

```python
# Apply Gaussian Blur

###
blur = cv2.GaussianBlur(edges, (5,5), 0)

plt.imshow(blur, cmap='gray')
plt.title('Gaussian Blur')
plt.axis('off')
plt.show()

###
```

---

###  Step 9: Hough Transform

```python
# Detect lines using Hough Transform

###
lines = cv2.HoughLinesP(
    blur, 1, np.pi/180, 50,
    minLineLength=50, maxLineGap=100
)

line_image = image.copy()

if lines is not None:
    for x1, y1, x2, y2 in lines.reshape(-1, 4):
        cv2.line(line_image, (x1,y1), (x2,y2), (255,0,0), 3)

plt.imshow(line_image)
plt.title('Detected Lines')
plt.axis('off')
plt.show()
###
```

---

### Step 10: Lane Detection Logic

```python
# Already implemented
# (Do not modify)
result = image.copy()

if lines is not None:
    for x1, y1, x2, y2 in lines.reshape(-1, 4):
        cv2.line(result, (x1,y1), (x2,y2), (0,255,0), 5)

plt.figure(figsize=(10,5))
plt.imshow(result)
plt.title('Final Lane Detection')
plt.axis('off')
plt.show()

print("Lane Detection Completed Successfully!")
```

---

##  Expected Output

* Original image
* Grayscale image
* Thresholded image
* ROI masked image
* Edge detected image
* Smoothed image
* Detected lines
* Final lane detection output
<img width="262" height="350" alt="image" src="https://github.com/user-attachments/assets/9578679a-3b3d-4e20-99dc-824304752da1" />

<img width="222" height="340" alt="image" src="https://github.com/user-attachments/assets/00e9f3c2-3c34-4215-a32a-be837656ea8c" />

<img width="301" height="345" alt="image" src="https://github.com/user-attachments/assets/63ac3316-d14f-4b4d-983e-474db38a5c14" />

<img width="310" height="355" alt="image" src="https://github.com/user-attachments/assets/1e5383e9-71a9-4b17-83cf-6bd665f5f9c4" />

<img width="311" height="386" alt="image" src="https://github.com/user-attachments/assets/b10b1f43-298c-433b-aa2b-7f98e07cd4d0" />

<img width="262" height="382" alt="image" src="https://github.com/user-attachments/assets/c8ef21f9-b097-4e0f-a0d5-ce027b497f55" />

<img width="257" height="385" alt="image" src="https://github.com/user-attachments/assets/bca071e5-94ec-46c7-abc4-257692864e4c" />

<img width="261" height="367" alt="image" src="https://github.com/user-attachments/assets/2fc62f62-7a00-48b1-8b6b-09311a57b3c1" />


---

##  Instructions

* Fill ONLY in `# Your Code Here` sections
* Do NOT change existing code
* Run step-by-step
* Verify outputs

---

## Result

Thus, the lane detection pipeline is successfully implemented by completing the missing code sections. The system detects and highlights lane lines effectively.

---

##  Developed By

* **Name:** ______MUTHU POORNIMA P______________________
* **Register No:** ____212224240099__________________
