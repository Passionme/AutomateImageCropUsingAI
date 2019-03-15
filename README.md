# AutomateImageCropUsingAI
Image Crop using Opencv python


This script can crop an image within the dark/black vertical and horizontal frame (as in a scanned/photographed copy)
It will detect the roi automatically and define the picture size to crop.

Input:
![](input/scanned%20input.png)

In te above image, the picture to be cropped is surrounded with vertical and horizontal blck strips. Identifying these regions will give the roi. Thus we can extract the roi from inout image to crop the actual image from a scanned copy.

Resulting in an output:
![](output/Crop%20output.png)

## How to Use
Folder Structure is important
1. In "input" folder place  images to be cropped 
2. Crop script as in "src" folder
3. Use the following command from command prompt

"python -m C:/.xx../src/CropImage.py

4. Crop image is placed in 'output' folder with defualt image name and file type.

Note: The script to crop image uses Opencv, Numpy. Mkae sure you ahve the latest versions instlled
