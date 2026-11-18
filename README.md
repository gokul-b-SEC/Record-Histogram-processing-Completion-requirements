# Experiment 03 – Histogram Equalization Using OpenCV

## AIM

To write a Python program using OpenCV to perform histogram equalization on both grayscale and colour images to enhance image contrast and brightness.

The program performs the following operations:

1. Read and display a grayscale image.
2. Plot the histogram of the grayscale image.
3. Apply histogram equalization to the grayscale image.
4. Read and display a colour image.
5. Plot histograms of the B, G and R channels.
6. Convert the image into HSV colour space.
7. Apply histogram equalization to the Value (V) channel.
8. Convert the enhanced image back to BGR format.
9. Display original and enhanced images with their histograms.

## SOFTWARE REQUIRED

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (`cv2`)
- NumPy
- Matplotlib

## ALGORITHM

**Step 1:** Import the required libraries: OpenCV, NumPy and Matplotlib.

**Step 2:** Read the image (`fly.png`) in grayscale format.

**Step 3:** Display the grayscale image and plot its histogram.

**Step 4:** Apply histogram equalization using `cv2.equalizeHist()` to enhance the image contrast.

**Step 5:** Display the original grayscale image, its histogram, the enhanced image and its histogram.

**Step 6:** Read the same image in colour format.

**Step 7:** Split the image into B, G and R channels and plot their histograms.

**Step 8:** Convert the image from BGR to HSV colour space using `cv2.cvtColor()`.

**Step 9:** Apply histogram equalization to the V (Value) channel using `cv2.equalizeHist()`.

**Step 10:** Merge the H, S and enhanced V channels and convert the image back to BGR format.

**Step 11:** Display the original colour image, enhanced colour image and their histograms.

---

## PROGRAM

### i) Read and display the grayscale image

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('fly.png', cv2.IMREAD_GRAYSCALE)

plt.imshow(img, cmap='gray')
plt.title('Original Image')
plt.show()
```

### ii) Plot the histogram of the grayscale image

```python
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Image Histogram')
plt.show()
```

### iii) Apply histogram equalization to the grayscale image

```python
img_eq = cv2.equalizeHist(img)

plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Equalized Histogram')

plt.imshow(img_eq, cmap='gray')
plt.title('Equalized Image')
plt.show()
```

### iv) Read the colour image and convert it into HSV colour space

```python
img = cv2.imread('fly.png', cv2.IMREAD_COLOR)

img_hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

img_hsv[:, :, 2] = cv2.equalizeHist(img_hsv[:, :, 2])

img_eq = cv2.cvtColor(img_hsv, cv2.COLOR_HSV2BGR)
```

### v) Display the enhanced colour image

```python
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Image')
plt.show()
```

### vi) Plot the histogram of the enhanced colour image

```python
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Histogram Equalized')
plt.show()
```

### vii) Display original and enhanced colour images

```python
plt.figure(figsize=(20, 10))

plt.subplot(221)
plt.imshow(img[:, :, ::-1])
plt.title('Original Color Image')

plt.subplot(222)
plt.imshow(img_eq[:, :, ::-1])
plt.title('Equalized Image')

plt.show()
```

### viii) Display original and equalized histograms

```python
plt.figure(figsize=[15, 4])

plt.subplot(121)
plt.hist(img.ravel(), 256, range=[0, 256])
plt.title('Original Image')

plt.subplot(122)
plt.hist(img_eq.ravel(), 256, range=[0, 256])
plt.title('Histogram Equalized')

plt.show()
```

---

## OUTPUT

The following outputs are obtained after executing the Python program:

1. Original grayscale image.
2. Histogram of the original grayscale image.
3. Histogram-equalized grayscale image.
4. Histogram of the equalized grayscale image.
5. Original colour image.
6. Enhanced colour image using HSV histogram equalization.
7. Original and enhanced colour image histograms.

### Output Screenshots

<img width="1436" height="414" alt="image" src="https://github.com/user-attachments/assets/8ac17dcb-1a55-40f8-9c8e-25a69dd7c073" />
<img width="1236" height="372" alt="image" src="https://github.com/user-attachments/assets/d276af3a-fc52-43ed-98ee-08ed9482a167" />
<img width="570" height="433" alt="image" src="https://github.com/user-attachments/assets/8e04a715-4b40-4745-a6e8-a4a28a1b32ec" />
<img width="570" height="433" alt="image" src="https://github.com/user-attachments/assets/0b309fa0-888d-49bc-b1a4-947ee0741092" />
<img width="552" height="388" alt="image" src="https://github.com/user-attachments/assets/4322a596-c246-4d1e-8343-698133f0975e" />


## RESULT

Thus, histogram equalization was successfully performed on both grayscale and colour images using Python and OpenCV. The contrast and brightness distribution of the images were enhanced using `cv2.equalizeHist()`, improving their visual appearance.
