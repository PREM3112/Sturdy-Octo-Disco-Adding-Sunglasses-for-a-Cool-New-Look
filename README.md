# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program:
### Name:PREM R
### Reg.no:212223240124

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage= cv2.imread("my image.jpg")
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
faceImage.shape
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
faceWithGlassesNaive = faceImage.copy()

# Replace the eye region with the sunglass image
faceWithGlassesNaive[150:210, 120:320] = glassBGR  # Matching (60,200,3)


plt.imshow(faceWithGlassesNaive[...,::-1])
# Make the dimensions of the mask same as the input image.
# Since Face Image is a 3-channel image, we create a 3 channel image for the mask
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))

# Make the values [0,1] since we are using arithmetic operations
glassMask = np.uint8(glassMask/255)

# Make a copy
faceWithGlassesArithmetic = faceImage.copy()

# Get the eye region from the face image
eyeROI= faceWithGlassesArithmetic[150:210, 120:320]

# Use the mask to create the masked eye region
maskedEye = cv2.multiply(eyeROI,(1-  glassMask ))

# Use the mask to create the masked sunglass region
maskedGlass = cv2.multiply(glassBGR,glassMask)

# Combine the Sunglass in the Eye Region to get the augmented image
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)

# Display the intermediate results
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
# Replace the eye ROI with the output from the previous section
faceWithGlassesArithmetic[150:210, 120:320]=eyeRoiFinal

# Display the final result
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");

```
## Output:
### 1.Original image:
![Screenshot 2025-03-11 180222](https://github.com/user-attachments/assets/0940dac3-6ed6-49ba-9ed2-23fea8450af8)


### 2.Glass:
![Screenshot 2025-03-11 180324](https://github.com/user-attachments/assets/5398b7ad-3dc4-4d0c-b4b7-62e5d48c73ee)


### 3.Glass color channel:
![Screenshot 2025-03-11 180405](https://github.com/user-attachments/assets/444504e9-c1d0-4bfa-bbb1-1519bcfe3a5d)


### 4.Face With Glass:
![Screenshot 2025-03-11 180447](https://github.com/user-attachments/assets/d192e6b3-ab6d-4e32-bb03-b905110bf094)


### 5.Eye and glass region:
![Screenshot 2025-03-11 180542](https://github.com/user-attachments/assets/95037664-e450-42c3-843d-d3127c2d08f3)


### 6.Final image with glass:
![image](https://github.com/user-attachments/assets/3f557dde-5fdd-4e1c-b41a-076b94a8b479)


## Result:
Thus, the creative project designed to overlay sunglasses on individual passport size photo has been successfully executed.
