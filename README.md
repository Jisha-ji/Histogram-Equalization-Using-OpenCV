# EX NO : 03 Histogram Equalization Using OpenCV (Grayscale & Color Images)
## Name: JISHA BOSSNE SJ

## Register No: 212224230106
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

**Name:** JISHA BOSSNE SJ

**Register No:** 212224230106



#### Grayscale Histogram Equalization

```
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the image in grayscale format
img = cv2.imread('parrot.jpg', cv2.IMREAD_GRAYSCALE)

# Plot histogram of original image
plt.figure(figsize=(10,8))

plt.subplot(2,2,1)
plt.imshow(img, cmap='gray')
plt.title('Original Grayscale Image')
plt.axis('off')

plt.subplot(2,2,2)
plt.hist(img.ravel(), bins=256, range=[0,256])
plt.title('Histogram of Original Image')

# Perform histogram equalization
equalized_img = cv2.equalizeHist(img)

# Display equalized image
plt.subplot(2,2,3)
plt.imshow(equalized_img, cmap='gray')
plt.title('Equalized Image')
plt.axis('off')

# Histogram of equalized image
plt.subplot(2,2,4)
plt.hist(equalized_img.ravel(), bins=256, range=[0,256])
plt.title('Histogram of Equalized Image')

plt.tight_layout()
plt.show()
```


#### Color Histogram Equalization (HSV Method)

```
# Import required libraries
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the color image
img = cv2.imread('parrot.jpg')

# Convert BGR to RGB for display
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.figure(figsize=(10,8))

# Original Image
plt.subplot(2,2,1)
plt.imshow(img_rgb)
plt.title('Original Color Image')
plt.axis('off')

# Plot histogram of original image (BGR channels)
plt.subplot(2,2,2)
color = ('b','g','r')
for i, col in enumerate(color):
    hist = cv2.calcHist([img], [i], None, [256], [0,256])
    plt.plot(hist, color=col)
plt.title('Histogram of Original Image')

# Convert to HSV
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

# Equalize only the V channel (brightness)
hsv[:,:,2] = cv2.equalizeHist(hsv[:,:,2])

# Convert back to BGR
enhanced_img = cv2.cvtColor(hsv, cv2.COLOR_HSV2BGR)

# Convert to RGB for display
enhanced_rgb = cv2.cvtColor(enhanced_img, cv2.COLOR_BGR2RGB)

# Display enhanced image
plt.subplot(2,2,3)
plt.imshow(enhanced_rgb)
plt.title('Enhanced Color Image')
plt.axis('off')

# Histogram of enhanced image
plt.subplot(2,2,4)
for i, col in enumerate(color):
    hist = cv2.calcHist([enhanced_img], [i], None, [256], [0,256])
    plt.plot(hist, color=col)
plt.title('Histogram of Enhanced Image')

plt.tight_layout()
plt.show()
```

---

##  Output

### Grayscale Histogram Equalization

- Original grayscale image is displayed  
- Histogram of original grayscale image is plotted  
- Enhanced image after histogram equalization is displayed  
- Histogram of enhanced grayscale image shows improved contrast

<img width="643" height="465" alt="image" src="https://github.com/user-attachments/assets/ff1fdbe4-decd-4940-8a96-32c3981ec4f4" />

<img width="732" height="520" alt="image" src="https://github.com/user-attachments/assets/c583ff41-1c64-4ae2-bbc8-31964c7d3898" />

<img width="640" height="462" alt="image" src="https://github.com/user-attachments/assets/f41e466e-4374-4c23-b4a9-871d0ca3e543" />

<img width="761" height="515" alt="image" src="https://github.com/user-attachments/assets/c02a4ba4-c6b3-4aa2-98bb-4ff72ea39048" />


### Color Image Histogram Equalization

- Original color image is displayed  
- Histogram of B, G, R channels is plotted  
- Enhanced image after HSV-based equalization is displayed  
- Histogram of enhanced image shows better intensity distribution  

<img width="639" height="458" alt="image" src="https://github.com/user-attachments/assets/61d542b4-87f7-4e11-ad64-eef4c8a38927" />

<img width="751" height="521" alt="image" src="https://github.com/user-attachments/assets/0b48eb6d-0c5e-4267-9275-8edbb5f2e24c" />

<img width="650" height="460" alt="image" src="https://github.com/user-attachments/assets/83aa8bea-a1cf-4941-ab65-ad525c246e14" />

<img width="734" height="525" alt="image" src="https://github.com/user-attachments/assets/dd052868-d689-42de-9a95-c8e3e43e0a56" />

---

## Result

Thus, histogram equalization is successfully performed on both grayscale and color images using OpenCV. The contrast and brightness of the images are significantly improved, enhancing visual quality and feature visibility.
