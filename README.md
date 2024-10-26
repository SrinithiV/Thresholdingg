# THRESHOLDING
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm
### Step1:
Load the input image using cv2.imread() and convert it to a grayscale image using cv2.cvtColor() with the color conversion code cv2.COLOR_BGR2GRAY.

### Step2:
Use a fixed threshold value (e.g., 127) for global thresholding with cv2.threshold(). Pixels with intensity above this value are set to maximum intensity (255), and the rest are set to minimum intensity (0).

### Step3:
Use adaptive thresholding, which calculates the threshold for smaller regions of the image. The threshold is calculated dynamically using cv2.adaptiveThreshold() with the ADAPTIVE_THRESH_GAUSSIAN_C method.

### Step4:
Otsu's method automatically finds an optimal threshold value by minimizing the within-class variance. Apply it using cv2.threshold() with the flag cv2.THRESH_OTSU.

### Step5:
Use plt.imshow() to visualize the grayscale image and the segmented images from global, adaptive, and Otsu's thresholding techniques.

## Program
### DEVELOPED BY : SRINITHI V
### REGISTER NO. : 212222110046
### Original Image
```python
import cv2
import matplotlib.pyplot as plt

image = cv2.imread('gray.jpg')
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.xticks([]), plt.yticks([])
plt.show()
```
### Output
![Screenshot 2024-10-26 114429](https://github.com/user-attachments/assets/c632ed45-4679-4b2d-a20d-dcc455a43364)

### Global Thresholding
```python
ret_global, th_global = cv2.threshold(gray_image, 127, 255, cv2.THRESH_BINARY)

plt.imshow(th_global, cmap='gray')
plt.title('Global Thresholding (v=127)')
plt.xticks([]), plt.yticks([])
plt.show()
```
### Output
![Screenshot 2024-10-26 114438](https://github.com/user-attachments/assets/fba309e2-5328-44b2-a8c4-defc5128022a)

### Adaptive Thresholding
```python
thresh_adaptive = cv2.adaptiveThreshold(gray_image, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY, 11, 2)

plt.imshow(thresh_adaptive, cmap='gray')
plt.title('Adaptive Gaussian Thresholding')
plt.xticks([]), plt.yticks([])
plt.show()
```
### Output
![Screenshot 2024-10-26 114448](https://github.com/user-attachments/assets/3b92dcf2-3c67-4c75-bbad-c734826bac08)

### Optimum Global Thesholding using Otsu's Method
```python
ret_otsu, th_otsu = cv2.threshold(gray_image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

plt.imshow(th_otsu, cmap='gray')
plt.title("Otsu's Thresholding")
plt.xticks([]), plt.yticks([])
plt.show()
```
### Output
![Screenshot 2024-10-26 114456](https://github.com/user-attachments/assets/91225680-88a3-47a8-b9a1-84306f996469)

## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.
