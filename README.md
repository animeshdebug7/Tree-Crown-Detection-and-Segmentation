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
Threshold the point cloud from the middle and create DSM of
middle layer.
