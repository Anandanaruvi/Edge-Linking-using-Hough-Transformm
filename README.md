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
### PROGRAM:
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
image = cv2.imread('waterfall.jpg')  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
edges = cv2.Canny(gray_image, 50, 150, apertureSize=3)
# Detect lines using the probabilistic Hough transform
lines = cv2.HoughLinesP(edges, rho=1, theta=np.pi/180, threshold=100, minLineLength=50, maxLineGap=10)

# Draw the lines on the original image
output_image = image.copy()

if lines is not None:
    for line in lines:
        x1, y1, x2, y2 = line[0]
        cv2.line(output_image, (x1, y1), (x2, y2), (0, 255, 0), 2)
# Displaying results using Matplotlib
plt.figure(figsize=(12, 12))
# Input Image and Grayscale Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Input Image')
plt.axis('off')
```


![image](https://github.com/user-attachments/assets/eb4f40fb-b3cc-4814-a217-cab999c8f35e)

![image](https://github.com/user-attachments/assets/4f051467-c91c-44b7-966b-7e414fa350de)

### # Canny Edge Detection Output:
```
# Canny Edge Detection Output
plt.imshow(edges, cmap='gray')
plt.title('Canny Edge Detector Output')
plt.axis('off')
```
### output:
![image](https://github.com/user-attachments/assets/e9127052-ae10-4ac9-bcd0-d2fbd7bc0d6f)


### Display the result of Hough transform.
### Hough Transform Result.
```
# Hough Transform Result
plt.imshow(cv2.cvtColor(output_image, cv2.COLOR_BGR2RGB))
plt.title('Hough Transform - Line Detection')
plt.axis('off')
```
![image](https://github.com/user-attachments/assets/ce8ce056-1b9c-4076-8c9c-c3eb3a690052)


### Result :
Thus the program is written with Python and OpenCV to detect lines using Hough transform.
