# edge-detection-opencv

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

---

## Software Required

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## ⚙️ Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using `cv2.imread()`.

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply **Sobel operator** using OpenCV to detect edges.

### Step 5:
Apply **Prewitt operator** using custom kernels.

### Step 6:
Apply **Roberts operator** using custom kernels.

### Step 7:
Apply **Laplacian operator** using OpenCV.

### Step 8:
Apply **Canny edge detector** using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

---

## Developed By

- **Name:** _______MUTHU POORNIMA P_____________________  
- **Register No:** ____212224240099__________________  
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
import os

# Step 2: Load image
path = os.path.expanduser("~/Downloads/exp6image.jpg")
img = cv2.imread(path)

if img is None:
    print("Image not found! Check the filename.")
else:
    # Step 3: Convert to grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Step 4: Sobel operator
    sobel_x = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
    sobel_y = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
    sobel = cv2.convertScaleAbs(cv2.addWeighted(
        cv2.convertScaleAbs(sobel_x), 0.5,
        cv2.convertScaleAbs(sobel_y), 0.5, 0
    ))

    # Step 5: Prewitt operator
    kx = np.array([[-1, 0, 1],
                   [-1, 0, 1],
                   [-1, 0, 1]])
    ky = np.array([[-1, -1, -1],
                   [ 0,  0,  0],
                   [ 1,  1,  1]])
    px = cv2.filter2D(gray, cv2.CV_32F, kx)
    py = cv2.filter2D(gray, cv2.CV_32F, ky)
    prewitt = cv2.convertScaleAbs(cv2.magnitude(px, py))

    # Step 6: Roberts operator
    rx = np.array([[1, 0],
                   [0, -1]], dtype=np.float32)
    ry = np.array([[0, 1],
                   [-1, 0]], dtype=np.float32)
    gx = cv2.filter2D(gray, cv2.CV_32F, rx)
    gy = cv2.filter2D(gray, cv2.CV_32F, ry)
    roberts = cv2.convertScaleAbs(cv2.magnitude(gx, gy))

    # Step 7: Laplacian operator
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    # Step 8: Canny edge detector
    canny = cv2.Canny(gray, 100, 200)

    # Step 9: Display all results
    titles = ["Original", "Grayscale", "Sobel",
              "Prewitt", "Roberts", "Laplacian", "Canny"]
    images = [cv2.cvtColor(img, cv2.COLOR_BGR2RGB),
              gray, sobel, prewitt, roberts, laplacian, canny]

    plt.figure(figsize=(12, 8))

    for i in range(len(images)):
        plt.subplot(2, 4, i + 1)
        plt.imshow(images[i], cmap="gray" if i > 0 else None)
        plt.title(titles[i])
        plt.axis("off")

    plt.tight_layout()
    plt.show()
```
---

## Output
## Original image:

<img width="336" height="380" alt="image" src="https://github.com/user-attachments/assets/66785b55-8094-4978-8504-e293839462fa" />

###  Sobel Edge Detector
- Detects edges in horizontal and vertical directions  
- Produces gradient-based edge map 

<img width="343" height="395" alt="image" src="https://github.com/user-attachments/assets/b88cabb0-e798-4df5-832b-eefa90011766" />


###  Prewitt Edge Detector
- Similar to Sobel but simpler kernel  
- Detects directional edges  

<img width="351" height="375" alt="image" src="https://github.com/user-attachments/assets/0ded02fd-4e63-423a-af07-15f2b7739c3b" />


###  Roberts Edge Detector
- Detects edges using diagonal gradients  
- Sensitive to noise  

<img width="341" height="385" alt="image" src="https://github.com/user-attachments/assets/64528f47-5c91-410f-b814-4d9a06689ccf" />


###  Laplacian Edge Detector
- Detects edges using second-order derivatives  
- Highlights rapid intensity changes  

<img width="342" height="391" alt="image" src="https://github.com/user-attachments/assets/81f7aac7-65d8-4632-b036-53a216d6da1c" />


###  Canny Edge Detector
- Multi-stage edge detection  
- Produces clean and thin edges  

<img width="340" height="398" alt="image" src="https://github.com/user-attachments/assets/a049a0ef-58ca-48e9-989f-643c3f64b212" />


---

## Result

Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
