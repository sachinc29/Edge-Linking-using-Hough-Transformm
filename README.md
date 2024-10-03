# Edge-Linking-using-Hough-Transformm
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:

Import all the necessary modules for the program.
### Step2:

Load a image using imread() from cv2 module.
### Step3:

Convert the image to grayscale.
### Step4:

Using Canny operator from cv2,detect the edges of the image.
### Step5:

Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program:
### Developed by: Sachin.C
### Reg no: 212222230125
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### Input image and grayscale image
```python
image = cv2.imread('badminton.jpg')  
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
plt.subplot(2, 2, 1)
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')

plt.subplot(2, 2, 2)
plt.imshow(gray_image, cmap='gray')
plt.title('Grayscale Image')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/7710a8f0-8a49-4808-bb86-a125e3dd4476)

![image](https://github.com/user-attachments/assets/6c0197a9-4b94-4e58-a7f5-7b0746c8e71d)

### Canny Edge detector 
```python
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)

plt.subplot(2, 2, 3)
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/f3d31cfc-7e9c-463f-8444-48c675836eda)


### Detect lines using the probabilistic Hough transform
```python

lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)
```
### Draw the lines on the original image
```python
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
```

### Hough Transform Result
```python
plt.subplot(2, 2, 4)
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/6bfb1cf6-8d68-4ce7-bb40-1a69568cc997)

## Result:
Thus, the program to detect the lines using Hough Transform implemented successfully.

