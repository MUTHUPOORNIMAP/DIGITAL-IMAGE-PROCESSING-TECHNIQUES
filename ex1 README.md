# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** MUTHU POORNIMA  
- **Register Number:** 212224240099

  ### Ex. No. 01

#### 1. Read the image ('dipt image.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.jpg")

img = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)

if img is None:
    print("Image not found. Check the filename in Downloads.")
else:
    print("Image dimensions:", img.shape)
    print("\nImage matrix:\n", img)

    plt.imshow(img, cmap="gray")
    plt.axis("off")
    plt.show()
```

#### 2. Print the image width, height & Channel.
```python
import cv2
import os

image_path = os.path.expanduser("~/Downloads/dipt image.jpg")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    height, width, channels = img.shape

    print("Width :", width)
    print("Height:", height)
    print("Channels:", channels)
```

#### 3. Display the image using matplotlib imshow().
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.jpg")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    plt.imshow(img_rgb)
    plt.title("Image Display")
    plt.axis("off")
    plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
import cv2
import os

image_path = os.path.expanduser("~/Downloads/dipt image.jpg")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    output_path = os.path.expanduser("~/Downloads/dipt image.png")

    success = cv2.imwrite(output_path, img)

    if success:
        print("Image saved successfully as 'dipt image.png'.")
    else:
        print("Error: Unable to save the image.")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.png")

img = cv2.imread(image_path, cv2.IMREAD_GRAYSCALE)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    color_img = cv2.cvtColor(img, cv2.COLOR_GRAY2BGR)

    plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
    plt.title("Color Image")
    plt.axis("off")
    plt.show()
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.png")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    color_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    height, width, channels = img.shape

    print("Width :", width)
    print("Height:", height)
    print("Channels:", channels)

    plt.imshow(color_img)
    plt.title("Dipt Image - Colour Image")
    plt.axis("off")
    plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.png")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    cropped = img[100:600, 200:900]

    if cropped.size == 0:
        print("Error: The crop area is outside the image boundaries.")
    else:
        cropped_rgb = cv2.cvtColor(cropped, cv2.COLOR_BGR2RGB)

        plt.imshow(cropped_rgb)
        plt.title("Cropped Dipt Image")
        plt.axis("off")
        plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.png")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    resized = cv2.resize(
        img, None,
        fx=2, fy=2,
        interpolation=cv2.INTER_LINEAR
    )

    resized_rgb = cv2.cvtColor(resized, cv2.COLOR_BGR2RGB)

    print("Original dimensions:", img.shape)
    print("Resized dimensions:", resized.shape)

    plt.imshow(resized_rgb)
    plt.title("Resized Image (2x)")
    plt.axis("off")
    plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
import cv2
import matplotlib.pyplot as plt
import os

image_path = os.path.expanduser("~/Downloads/dipt image.png")

img = cv2.imread(image_path)

if img is None:
    print("Error: Unable to load the image. Check the filename and path.")
else:
    resized = cv2.resize(
        img, None,
        fx=2, fy=2,
        interpolation=cv2.INTER_LINEAR
    )

    resized_rgb = cv2.cvtColor(resized, cv2.COLOR_BGR2RGB)

    print("Original dimensions:", img.shape)
    print("Resized dimensions:", resized.shape)

    plt.imshow(resized_rgb)
    plt.title("Resized Image (2x)")
    plt.axis("off")
    plt.show()
```
## OUTPUT:
1. 

<img width="716" height="590" alt="image" src="https://github.com/user-attachments/assets/33db3521-155a-4297-b4a9-c6d98728aa0b" />

2.

<img width="145" height="76" alt="image" src="https://github.com/user-attachments/assets/ab4e69ac-1517-4596-aa34-9da0a8fee8a8" />

3.

<img width="660" height="412" alt="image" src="https://github.com/user-attachments/assets/f6500f05-1bbe-4a7c-9857-1b6687c588ff" />

4.

<img width="447" height="45" alt="image" src="https://github.com/user-attachments/assets/8878c0ec-fbdd-4c43-ba40-196f31bdc150" />

5.

<img width="651" height="412" alt="image" src="https://github.com/user-attachments/assets/36ec5841-7440-47df-ac18-8825b82e4ed6" />

6.

<img width="661" height="478" alt="image" src="https://github.com/user-attachments/assets/d42026f9-41b8-4a96-82f2-4c6878fd049a" />

7.

<img width="642" height="426" alt="image" src="https://github.com/user-attachments/assets/e5599bd6-1ea0-499c-ab9b-bbf3fcc70e71" />

8.

<img width="650" height="445" alt="image" src="https://github.com/user-attachments/assets/788724ec-046d-4f9f-a672-7db1976de055" />

### Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.
