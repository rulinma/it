# opencv

https://github.com/opencv/opencv

## 使用

推荐
$ conda install conda-forge::opencv -y

或者
$ pip install opencv-python

``` python
import cv2

img = cv2.imread('rose.jpg')

print("Image Properties")
print("- Number of Pixels: " + str(img.size))
print("- Shape/Dimensions: " + str(img.shape))

```

```
Image Properties
- Number of Pixels: 2782440
- Shape/Dimensions: (1180, 786, 3)
```

``` python
import cv2
import numpy as np
from matplotlib import pyplot as plt

# Declaring the output graph's size
plt.figure(figsize=(16, 16))

# Convert image to grayscale
img_gs = cv2.imread('cat.jpg', cv2.IMREAD_GRAYSCALE)
cv2.imwrite('gs.jpg', img_gs)

# Apply canny edge detector algorithm on the image to find edges
edges = cv2.Canny(img_gs, 100,200)

# Plot the original image against the edges
plt.subplot(121), plt.imshow(img_gs)
plt.title('Original Gray Scale Image')
plt.subplot(122), plt.imshow(edges)
plt.title('Edge Image')

# Display the two images
plt.show()

```

## 参考文献

1. <https://opencv.org/>
2. [Python 教程之如何用 OpenCV 处理图像](https://www.freecodecamp.org/chinese/news/image-processing-with-opencv)
