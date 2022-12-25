# Tree-Crown-Detection-and-Segmentation

## About
A technique is developed for identifying individual tree crowns from airborne LiDAR data. The method is used to delineate tree crowns using a region-growing algorithm after initially identifying tree tops in the rasterised middle and top layer of the point cloud.The accuracy is measured through the estimated values and the ground truth.

|Developed By|
|:-|
|[Animesh Singh](https://github.com/animeshdebug7) (me)|
|[Vidhan Jain](https://github.com/vidhanjain03)|

**`Under supervision of Dr. Anand S. Sahadevan, Scientist, SAC, ISRO, Ahmedabad, India`**

## Methodology

**`Step 1`**
Threshold the point cloud from the middle and create DSM of middle layer.

<img src='files for readme\step1.png' width='600'>

**`Step 2`**
Applying binary morphological operations. First binary closing and then dilation is applied. In binary closing, erosion occurs followed by dilation. Erosion eliminates the outliers, whereas dilation fills in the black pixels between the crowns and stems.

<img src='files for readme\step2.png' width='600'>

**`Step 3`**
Find the centroid for every object in the image. These are seed_1.

<img src='files for readme\step3.png' width='600'>

**`Step 4`**
Take the top layer CHM and smooth the image

<img src='files for readme\step4.png' width='600'>

**`Step 5`**
Overlap seed_1 on the top layer CHM

<img src='files for readme\step5.png' width='600'>

**`Step 6`**
Make a window around each seed_1 and find the highest intensity pixel in that window(seed_2).

<img src='files for readme\step6.png' width='600'>

**`Step 7`**
Replace small clusters of seed_2 with single seed. That is our tree top.

<img src='files for readme\step7.png' width='600'>
