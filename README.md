# Histogram Equalization Using OpenCV

## Aim

To obtain a histogram for finding the frequency of pixels in an image with pixel values ranging from 0 to 255. Also, to write the code using OpenCV to perform histogram equalization.

## 🛠️ Software Used

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ⚙️ Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image and convert it to grayscale format.

### Step 3:
Display the grayscale image and plot its histogram.

### Step 4:
Apply histogram equalization using `cv2.equalizeHist()` to enhance contrast.

### Step 5:
Display the original grayscale image, its histogram, enhanced image, and enhanced histogram using a 2 × 2 grid.

### Step 6:
Read and display the same image in color format.

### Step 7:
Split the image into B, G, R channels and plot their histograms.

### Step 8:
Convert the image from BGR to HSV color space.

### Step 9:
Apply histogram equalization on the V (Value) channel.

### Step 10:
Merge the channels and convert the image back to BGR format.

### Step 11:
Display the original color image, its histogram, enhanced image, and enhanced histogram.

## 💻 Program

The Python program uses OpenCV to calculate image histograms and perform grayscale and color histogram equalization.

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Image path
image_path = r"C:\Users\acer\images\Boy.jpg"

# Read the image
img = cv2.imread(image_path)

if img is None:
    print("Image not found! Check the image path.")
else:
    print("Image loaded successfully!")

    # Convert to grayscale
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    # Grayscale histogram equalization
    equalized = cv2.equalizeHist(gray)

    # Display grayscale images and histograms
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(gray, cmap="gray")
    plt.title("Original Grayscale Image")
    plt.axis("off")

    plt.subplot(2, 2, 2)
    plt.hist(gray.ravel(), bins=256, range=(0, 256))
    plt.title("Original Grayscale Histogram")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")

    plt.subplot(2, 2, 3)
    plt.imshow(equalized, cmap="gray")
    plt.title("Equalized Grayscale Image")
    plt.axis("off")

    plt.subplot(2, 2, 4)
    plt.hist(equalized.ravel(), bins=256, range=(0, 256))
    plt.title("Equalized Grayscale Histogram")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")

    plt.tight_layout()
    plt.show()

    # Color image histogram
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    b, g, r = cv2.split(img)

    plt.figure(figsize=(12, 5))

    plt.subplot(1, 2, 1)
    plt.imshow(img_rgb)
    plt.title("Original Color Image")
    plt.axis("off")

    plt.subplot(1, 2, 2)
    plt.hist(b.ravel(), bins=256, range=(0, 256),
             color="blue", alpha=0.5, label="Blue")
    plt.hist(g.ravel(), bins=256, range=(0, 256),
             color="green", alpha=0.5, label="Green")
    plt.hist(r.ravel(), bins=256, range=(0, 256),
             color="red", alpha=0.5, label="Red")
    plt.title("B, G, R Channel Histograms")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")
    plt.legend()

    plt.tight_layout()
    plt.show()

    # Convert to HSV and equalize the Value channel
    hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
    h, s, v = cv2.split(hsv)

    v_equalized = cv2.equalizeHist(v)
    hsv_equalized = cv2.merge((h, s, v_equalized))
    enhanced_color = cv2.cvtColor(
        hsv_equalized, cv2.COLOR_HSV2RGB
    )

    # Display original and enhanced color histograms
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 2, 1)
    plt.imshow(img_rgb)
    plt.title("Original Color Image")
    plt.axis("off")

    plt.subplot(2, 2, 2)
    plt.hist(v.ravel(), bins=256, range=(0, 256))
    plt.title("Original V Channel Histogram")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")

    plt.subplot(2, 2, 3)
    plt.imshow(enhanced_color)
    plt.title("Histogram Equalized Color Image")
    plt.axis("off")

    plt.subplot(2, 2, 4)
    plt.hist(v_equalized.ravel(), bins=256, range=(0, 256))
    plt.title("Equalized V Channel Histogram")
    plt.xlabel("Pixel Intensity")
    plt.ylabel("Frequency")

    plt.tight_layout()
    plt.show()


### Developed By:

**Name:** Shaajini n

### Register No: 212225040395

---

## Output

### i) Grayscale Histogram Equalization

The original grayscale image and its histogram are displayed. Histogram equalization is applied to improve contrast, and the enhanced image and histogram are displayed.
<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/030ce0f0-596a-48b8-8d62-e25309aacdb4" />

### ii) Color Image Histogram

The original color image is displayed, and the histograms of the Blue, Green, and Red channels are plotted.

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/29c1e48c-5708-4eb1-aad1-38d20a11e80c" />


### iii) Color Histogram Equalization

The image is converted to HSV color space, and histogram equalization is applied to the Value (V) channel. The enhanced color image and its histogram are displayed.

<img width="1917" height="1078" alt="image" src="https://github.com/user-attachments/assets/bb2107f6-4231-4af8-b688-7f6977d08f26" />


---

## Result

Thus, histograms were obtained to determine the frequency of pixel intensities ranging from 0 to 255. Histogram equalization was successfully performed on grayscale and color images using OpenCV to improve image contrast.
