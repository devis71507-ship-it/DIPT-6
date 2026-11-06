# EDGE DETECTION

## Aim

To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required

- Anaconda – Python 3.7
- Jupyter Notebook / VS Code
- OpenCV (cv2)
- NumPy
- Matplotlib
  
## Algorithm

### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using cv2.imread().

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply Sobel operator using OpenCV to detect edges.

### Step 5:
Apply Prewitt operator using custom kernels.

### Step 6:
Apply Roberts operator using custom kernels.

### Step 7:
Apply Laplacian operator using OpenCV.

### Step 8:
Apply Canny edge detector using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

### Developed By
#### Name: DEVI S
#### Register No: 212225100008

## Program

```
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\sdhan\Downloads\WhatsApp Image 2026-10-17 at 3.09.40 PM.jpeg") 
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
```
<img width="268" height="360" alt="image" src="https://github.com/user-attachments/assets/c1e0a036-3872-4387-baa9-ed2ec8ff7247" />


### Sobel Edge Detector
- Detects edges in horizontal and vertical directions
- Produces gradient-based edge map

```
sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')
```
<img width="272" height="371" alt="image" src="https://github.com/user-attachments/assets/450f706b-a544-4b00-bcba-46b147f6411a" />


### Prewitt Edge Detector
- Similar to Sobel but simpler kernel
- Detects directional edges

```
image = cv2.imread(r"C:\Users\sdhan\Downloads\WhatsApp Image 2026-10-17 at 3.09.40 PM.jpeg")

gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

prewitt_x = np.array([[-1, 0, -1],
                      [ 1, 0, -1],
                      [ 1, 0, -1]])

prewitt_y = np.array([[ 1,  1,  1],
                      [ 0,  0,  0],
                      [-1, -1, -1]])

prewitt_x_edge = cv2.filter2D(gray, -1, prewitt_x)
prewitt_y_edge = cv2.filter2D(gray, -1, prewitt_y)

prewitt = cv2.magnitude(prewitt_x_edge.astype(np.float32),
                        prewitt_y_edge.astype(np.float32))

plt.imshow(prewitt, cmap='gray')
plt.title('Prewitt Edge Detection')
plt.axis('off')
plt.show()
```
<img width="247" height="318" alt="image" src="https://github.com/user-attachments/assets/35cdea06-c931-484b-b32a-0d74cff6203a" />


### Roberts Edge Detector
- Detects edges using diagonal gradients
- Sensitive to noise

```
roberts_x = np.array([[1, 0],
                      [0, -1]])

roberts_y = np.array([[0, 1],
                      [-1, 0]])

roberts_x_edge = cv2.filter2D(gray, -1, roberts_x)
roberts_y_edge = cv2.filter2D(gray, -1, roberts_y)

roberts = cv2.magnitude(
    roberts_x_edge.astype(np.float32),
    roberts_y_edge.astype(np.float32)
)

plt.imshow(roberts, cmap='gray')
plt.title('Roberts Edge Detection')
plt.axis('off')
plt.show()
```
<img width="263" height="332" alt="image" src="https://github.com/user-attachments/assets/99ec4eb7-228e-49df-9977-2b13bc4a49fd" />


### Laplacian Edge Detector
- Detects edges using second-order derivatives
- Highlights rapid intensity changes

```
Laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)

plt.imshow(Laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')
plt.show()
```
<img width="237" height="328" alt="image" src="https://github.com/user-attachments/assets/29b0f1eb-6f2b-4862-be7e-8c60bf19da86" />


  
### Canny Edge Detector

- Multi-stage edge detection
- Produces clean and thin edges

```
Canny_edges = cv2.Canny(gray_image, 50, 150)

plt.imshow(Canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')
plt.show()
```
<img width="253" height="332" alt="image" src="https://github.com/user-attachments/assets/1f2765b2-ee14-47ae-a63b-a7604ea5189e" />


  
## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
