# Image-enhancement-filters-opencv
# Image Smoothing and Sharpening Using OpenCV

# AIM
To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

# The program performs the following operations:
Read and display an input image
Apply Averaging filter
Apply Weighted Averaging filter
Apply Gaussian filter
Apply Median filter
Apply Laplacian sharpening using kernel
Apply Laplacian operator
Display all outputs for comparison

# Software Used
Anaconda – Python 3.7
Jupyter Notebook / VS Code
OpenCV (cv2)
NumPy
Matplotlib

# Algorithm
Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

Step 2:
Read the input image (e.g., image.jpg).

Step 3:
Convert the image from BGR to RGB format for display.

Step 4:
Apply Averaging Filter using cv2.blur().

Step 5:
Apply Weighted Averaging Filter using a custom kernel with cv2.filter2D().

Step 6:
Apply Gaussian Filter using cv2.GaussianBlur().

Step 7:
Apply Median Filter using cv2.medianBlur().

Step 8:
Apply Laplacian Sharpening using Kernel with cv2.filter2D().

Step 9:
Convert image to grayscale and apply Laplacian Operator using cv2.Laplacian().

Step 10:
Display all filtered images using a grid layout for comparison.

# Developed By
# Name: Kruthika R
# Register No: 212225240075
# Program
1. Smoothing Filters
# i) To display original image
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
image_path = r"C:\Users\kruthika\OneDrive\Dev\courses\College\DIPT.ipynb\mini cooper.jpg"

img = cv2.imread(image_path)

if img is None:
    print("Image not found! Check the path.")
else:
    print("Image loaded successfully!")
    print("Image size:", img.shape)
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(rgb)
plt.title("Original Image")
plt.axis('off')
plt.show()
```
<img width="827" height="582" alt="image" src="https://github.com/user-attachments/assets/fb26163b-4236-410c-b7c2-32acceb57ce5" />


# ii) Averaging filter
```
averaging = cv2.blur(img, (5, 5))

plt.imshow(cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB))
plt.title("Averaging Filter")
plt.axis('off')
plt.show()
```

<img width="815" height="591" alt="image" src="https://github.com/user-attachments/assets/24866d52-66d8-4b56-89f1-3efa864521bf" />

# iii) Weighted Averaging Filter
```
kernel = np.array([
    [1, 2, 1],
    [2, 4, 2],
    [1, 2, 1]
], dtype=np.float32) / 16

weighted = cv2.filter2D(img, -1, kernel)

plt.imshow(cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB))
plt.title("Weighted Averaging Filter")
plt.axis('off')
plt.show()
```

<img width="815" height="577" alt="image" src="https://github.com/user-attachments/assets/55ab5d10-ce32-4416-bbf7-4cbe20e20ccc" />

# iv) Gaussian Filter
```
gaussian = cv2.GaussianBlur(img, (5, 5), 0)

plt.imshow(cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB))
plt.title("Gaussian Filter")
plt.axis('off')
plt.show()
```
<img width="816" height="592" alt="image" src="https://github.com/user-attachments/assets/70b52881-1da5-4a35-b86b-dd3b67dd3b6e" />

# Median filter
```
median = cv2.medianBlur(img, 5)

plt.imshow(cv2.cvtColor(median, cv2.COLOR_BGR2RGB))
plt.title("Median Filter")
plt.axis('off')
plt.show()
```

<img width="817" height="592" alt="image" src="https://github.com/user-attachments/assets/e9a62bc8-5c1d-4bbe-b7f7-20b89dc9657a" />

# 2. Sharpening Filters

# i) Laplacian Sharpening
```
laplacian_kernel = np.array([
    [0, -1, 0],
    [-1, 5, -1],
    [0, -1, 0]
], dtype=np.float32)

sharpened = cv2.filter2D(img, -1, laplacian_kernel)

plt.imshow(cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB))
plt.title("Laplacian Sharpening")
plt.axis('off')
plt.show()
```

<img width="820" height="596" alt="image" src="https://github.com/user-attachments/assets/fd2f4927-bb53-462f-a993-1b63962afe46" />

# ii) Laplacian Operator

```
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

laplacian = cv2.Laplacian(gray, cv2.CV_64F)
laplacian = cv2.convertScaleAbs(laplacian)

plt.imshow(laplacian, cmap='gray')
plt.title("Laplacian Operator")
plt.axis('off')
plt.show()
```

<img width="812" height="590" alt="image" src="https://github.com/user-attachments/assets/01ff8e9a-4821-4727-8146-342055af2044" />

# comparing the outputs
```
images = [
    (rgb, "Original Image"),
    (cv2.cvtColor(averaging, cv2.COLOR_BGR2RGB), "Averaging Filter"),
    (cv2.cvtColor(weighted, cv2.COLOR_BGR2RGB), "Weighted Averaging"),
    (cv2.cvtColor(gaussian, cv2.COLOR_BGR2RGB), "Gaussian Filter"),
    (cv2.cvtColor(median, cv2.COLOR_BGR2RGB), "Median Filter"),
    (cv2.cvtColor(sharpened, cv2.COLOR_BGR2RGB), "Laplacian Sharpening"),
    (laplacian, "Laplacian Operator")
]

plt.figure(figsize=(14, 10))

for i, (image, title) in enumerate(images, 1):
    plt.subplot(2, 4, i)

    if title == "Laplacian Operator":
        plt.imshow(image, cmap='gray')
    else:
        plt.imshow(image)

    plt.title(title)
    plt.axis('off')

plt.tight_layout()
plt.show()
```

<img width="1368" height="692" alt="image" src="https://github.com/user-attachments/assets/6b9062e3-c18a-41b7-b125-2b963f675953" />
