# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step1:
Load the image and convert the image to Grayscale.

### Step2:
Smoothen the image using Gaussian Method.

### Step3:
Apply thresholding cv2.THRESH_BINARY on the image.

### Step4:
Apply thresholding cv2.THRESH_BINARY_INC on the image.

### Step5:
Apply thresholding cv2.THRESH_TRUNC on the image.

### step6:
Apply thresholding cv2.THRESH_TOZERO on the image.

## Program

```python
# Load the necessary packages
import cv2
import matplotlib.pyplot as plt
# Read the Image and convert to grayscale
BGR_image=cv2.imread('2.jpg')
gray=cv2.cvtColor(BGR_image,cv2.COLOR_BGR2GRAY)
plt.imshow(gray)
# Use Global thresholding to segment the image
ret,thresh1=cv2.threshold(gray,100,255,cv2.THRESH_BINARY )
ret,thresh2=cv2.threshold(gray,100,255,cv2.THRESH_BINARY_INV)
ret,thresh3=cv2.threshold(gray,100,255,cv2.THRESH_TRUNC)
ret,thresh4=cv2.threshold(gray,100,255,cv2.THRESH_TOZERO)
ret,thresh5=cv2.threshold(gray,100,255,cv2.THRESH_TOZERO_INV)
# Use Adaptive thresholding to segment the image
img= cv2.GaussianBlur(gray,(3,3),0)
th1 = cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY, 11,2) 
th2= cv2.adaptiveThreshold(gray, 255, cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY, 11,2)
titles = ['Original Image', 'Adaptive Mean Thresholding', "Adaptive Gaussian Thresholding"]
images =[img, th1, th2]
for i in range(3):
          plt.subplot (3,1,i+1),
          plt.imshow(images[i], 'gray')
          plt.title(titles[i])
          plt.xticks([]),plt.yticks([])
          plt.show()
# Use Otsu's method to segment the image 
ret2,th2 = cv2.threshold(gray,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)
# Display the results
plt.imshow(thresh1,cmap='gray')
plt.imshow(thresh2,cmap='gray')
plt.imshow(thresh3,cmap='gray')
plt.imshow(thresh4,cmap='gray')
plt.imshow(thresh5,cmap='gray')
plt.imshow(th2,cmap='gray')



```
## Output

### Original Image
![output](maple1.png)

### Global Thresholding
![output](maple2.png)

![ss1](https://user-images.githubusercontent.com/94828147/175765341-249ed42c-3c9e-4670-9e20-2defcaa93a10.png)

![ss2](https://user-images.githubusercontent.com/94828147/175765346-dd45628b-0296-47f6-8629-3ab73abd1289.png)

![ss3](https://user-images.githubusercontent.com/94828147/175765348-34271db3-f278-428c-be08-a934daea6a51.png)

![ss4](https://user-images.githubusercontent.com/94828147/175765349-7a646e02-69af-472d-97b8-cdf82b1e136d.png)

![ss5](https://user-images.githubusercontent.com/94828147/175765350-7b875860-6514-481b-b2ea-0c20f10a0113.png)

![ss6](https://user-images.githubusercontent.com/94828147/175765351-644ce77c-7bbd-4404-ba90-64cfd1cbadad.png)

### Adaptive Thresholding
![output](maple3.png)

### Optimum Global Thesholding using Otsu's Method
![output](maple4.png)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

