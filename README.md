# Tree-Crown-Detection-and-Segmentation

## About
This method is for identifying individual tree crowns from airborne LiDAR data. The method is used to delineate tree crowns using a region-growing algorithm after initially identifying tree tops in the rasterised middle and top layer of the point cloud.The accuracy is measured through the estimated values and the ground truth.

|Developed By|
|:-|
|[Vidhan Jain](https://github.com/vidhanjain03) (me)|
|[Animesh Singh](https://github.com/animeshdebug7)|


**`Under supervision of Dr. Anand S. Sahadevan, Scientist, SAC, ISRO, Ahmedabad, India`**

## Methodology

**`Step 1`**
Threshold the point cloud from the middle and create DSM of middle layer.
<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488018-0b362092-918b-4bb4-9562-fdf54ab8ffd3.png" width=50% height=50%>
</p>

**`Step 2`**
Applying binary morphological operations. First binary closing and then dilation is applied. In binary closing, erosion occurs followed by dilation. Erosion eliminates the outliers, whereas dilation fills in the black pixels between the crowns and stems.

<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488863-75a84601-b184-4482-9cad-f616ec4e0d33.png" width=50% height=50%>
</p>

**`Step 3`**
Find the centroid for every object in the image. These are seed_1.

<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488870-ba0725d2-40d7-49fc-a004-3157514f1c7c.png" width=50% height=50%>
</p>

**`Step 4`**
Take the top layer CHM and smooth the image

<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488881-40f37f96-2b31-4868-90b6-b70492b690b4.png" width=50% height=50%>
</p>

**`Step 5`**
Overlap seed_1 on the top layer CHM

<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488884-7ffcdd0f-73ba-40e3-9779-b3b3f72b5021.png" width=50% height=50%>
</p>

**`Step 6`**
Make a window around each seed_1 and find the highest intensity pixel in that window(seed_2).
<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488897-7d15de63-0ffc-43a5-acc2-c524debdaa58.png" width=50% height=50%>
</p>

**`Step 7`**
Replace small clusters of seed_2 with single seed. That is our tree top.

<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210488903-baae84b0-6a2e-4016-ad23-14613172772f.png" width=50% height=50%>
</p>

## Output
The following results were obtained using the watershed segmentation
<p align="center">
<img src="https://user-images.githubusercontent.com/66486050/210489772-daecd919-630a-4291-85c1-3e40946dc43f.png" width=50% height=50%>
</p>

## Findings
We have described the technique which has produced relatively precise results compared to other pre-existing methods. The accuracy of this method recedes when canopy is too small and adjoint because when large morphological kernel is used, more than one tree trunk will merge. For a small kernel, one tree will have more than one seed. To counter this problem, we take kernel size to distinguish two tree trunks and when more than one seed point for a single tree is observed, the cluster is replaced by a single seed. When canopies are larger, the accuracy increases. In the graph, plot 1, plot 3 estimated values are more deviated compared to plot 4 as these plots are of smaller canopies in a dense forest. The parameters of plots vary according to species of tree, sun position, slope of terrain, density of forest and other environmental conditions. The patch size for seed2 is taken between 50 - 100 as the image resolution is 2cm implying the tree top is going to be in the radius of 1 - 2 metres. The accurate tree tops is used in the region based image segmentation algorithm.
