# Image Mosaicing
![image](https://github.com/user-attachments/assets/c0389124-39f5-461a-98e1-fe3dfd097ad9)
![image](https://github.com/user-attachments/assets/84e9b44f-2453-4440-a7d4-2839f7039180)

## Overview

This project demonstrates image mosaicing, where multiple images are combined into a single cohesive mosaic. The process involves detecting corner features in images, finding correspondences between these features, estimating a homography matrix, and then stitching the images together. The resulting mosaic displays the union of all pixels from the input images.

## Key Components

1. **Harris Corner Detection**: The Harris corner detector identifies corner features in the images. Non-maximum suppression is applied to refine the feature points.
   
2. **Feature Matching**: Correspondences between features in different images are determined using Normalized Cross-Correlation (NCC). High NCC values indicate likely feature matches.
   
3. **Homography Estimation**: A homography matrix is estimated from matched features. RANSAC is used to robustly estimate the homography by filtering out outliers.

4. **Image Warping and Blending**: One image is warped into the coordinate system of another using the estimated homography. Overlapping pixels are blended to produce a seamless mosaic.

## Requirements

- Python 3.x
- OpenCV
- NumPy

## Installation

Ensure you have Python and the required libraries installed. You can install the required libraries using pip:

```bash
pip install numpy opencv-python
```

## USAGE

### 1. Setup

Ensure you have the required dependencies installed. You can install them using pip:

```bash
pip install numpy opencv-python
```
## Preparing Your Data

To use this project effectively, follow these steps to prepare your data:

1. **Organize Your Images**

   - Collect all the images you want to process and place them in a single directory. Make sure the images are in a format supported by OpenCV (e.g., PNG, JPEG).

   - Example directory structure:
     ```
     /path/to/images/
         image1.jpg
         image2.jpg
         image3.jpg
         ...
     ```

2. **Image Naming and Format**

   - Ensure that the images are named consistently if processing in a specific order or grouping. All images should be of the same format to avoid compatibility issues.

3. **Update Script Paths**

   - Modify the `path_to_images` variable in the script to point to your image directory:

     ```python
     path_to_images = r"your/path/to/images"
     ```

4. **Preprocess Images (Optional)**

   - Depending on your specific needs, you might need to preprocess the images. This could include tasks such as resizing, converting to grayscale, or applying filters. Ensure that any preprocessing steps are uniformly applied to all images.

5. **Verify Image Integrity**

   - Ensure that the images are not corrupted and are compatible with OpenCV. You can manually open them or use a script to check their integrity.

## Running the Code

1. **Set the Path to Your Images**

   In the `__main__` section of the code, update the `path_to_images` variable with the path to your image directory:

   ```python
   path_to_images = r"your/path/to/images"

2. **Adjust Parameters**

   Modify the parameters in the `ImageMosaicing` instance if needed. For example:

   ```python
   inst = ImageMosaicing(
       [g_1, g_2],                 # List of grayscale images
       "sobel",                    # Type of derivative filter (e.g., "sobel" or "prewitt")
       (5, 5),                     # Harris corner detector window size
       100000,                     # NCC threshold for feature matching
       (7, 7),                     # NCC window size
       1000                        # Number of RANSAC iterations
   )

### Run the Script

Execute the script to generate and display the mosaic:

```bash
python image_mosaicing.py
