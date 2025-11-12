# Edge Linking using Hough Transformm
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
### Program:

#### DEVELOPED BY: Priya Varshini P
#### REG NO:212224240119

#### Read image and convert it to grayscale image
```python
import numpy as np
import cv2
import matplotlib.pyplot as plt
img=cv2.imread("c1.jpg",0)
img_c=cv2.imread("c1.jpg",1)
img_c=cv2.cvtColor(img_c,cv2.COLOR_BGR2RGB)
gray=cv2.cvtColor(img,cv2.COLOR_GRAY2RGB)
gray = cv2.GaussianBlur(gray,(3,3),0)
plt.figure(figsize=(13,13))
plt.subplot(1,2,1)
plt.imshow(img_c)
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(gray)
plt.title("Gray Image")
plt.axis("off")
plt.show()
```
#### Find the edges in the image using canny detector and display
```python
canny=cv2.Canny(gray,120,150)
plt.imshow(canny)
plt.title("Canny Edge Detector")
plt.axis("off")
plt.show()
```
#### Detect points that form a line using HoughLinesP
```python
lines=cv2.HoughLinesP(canny,1,np.pi/180,threshold=80,minLineLength=50,maxLineGap=250)
```
#### Draw lines on the image
```python
for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(img_c,(x1,y1),(x2,y2),(255,0,0),3)
```
#### Display the result
```python
plt.imshow(img_c)
plt.title("Result Image")
plt.axis("off")
plt.show()
```
### Output

#### Input image and grayscale image

<img width="653" height="459" alt="Screenshot 2025-11-12 101841" src="https://github.com/user-attachments/assets/bbf13a7a-3e65-4879-add2-2c6e0576784d" />



#### Canny Edge detector output

<img width="178" height="265" alt="Screenshot 2025-11-12 102007" src="https://github.com/user-attachments/assets/bcb3a3e0-c687-4313-adc8-62e562ed280d" />


#### Display the result of Hough transform

<img width="180" height="263" alt="Screenshot 2025-11-12 102107" src="https://github.com/user-attachments/assets/44ec2355-ecb2-4f46-9c9b-f43b59079c60" />


### Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform.
