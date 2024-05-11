# Image_Segmentation


## Efficient Graph Based Algorithm

The algorithm that we start with is an Efficient Graph Based Algorithm. The algorithm is 
based on similarity and dissimilarity of elements in a component. As the image is transformed 
into a graph with pixels as nodes and edges connecting these pixels, we want the edges between 
two nodes in the same component to have low weights and, edges between different 
components to have high weights. 

The algorithm follows a greedy approach and compares edge nodes based on their internal 
difference and difference between components. If edge nodes belong to different components 
and their internal difference is less than the component difference, then we merge the nodes, 
otherwise, we do nothing. To control the degree to which the difference between two 
components must be greater, threshold function is used.

## Graph based Algorithm with Mean shift Filtering

We try another approach to improve the performance of the previous graph-based algorithm. 
We apply Mean shift Filtering before applying graph-based algorithm. Also, a gaussian 
filter is applied to improve performance as shown by previous results. The primary idea in 
Mean Shift algorithm is to shift data points iteratively towards the mode of the underlying 
probability density function.
The Mean Shift algorithm has several advantages, including its ability to handle irregularly 
shaped clusters and adapt to varying cluster densities. Food images tend to have irregular 
shaped clusters and thus, Mean Shift is a good choice.

## Graph based Algorithm with Mean shift and Background mask

After evaluating the results of previous two algorithms, we observed that our algorithms can’t 
distinguish between the background and foreground in the image. In order to fix this weakness 
of our algorithm, we use threshold processing to separate the background from the original 
image and add it to the segmented image after applying graph-based algorithm.
To get the background mask, we first convert the image to grayscale. Then, we apply Otsu’s 
thresholding technique and inverse the result. Next, to clean the object’s outline, we perform 
morphological opening operation. Morphological Open operation means shrinking the bright 
regions first, and then expanding them. Finally, to get a hold of the background, we dilate the 
image which expands the bright regions. Then, perform Distance Transform which calculates 
the distance of each white pixel to the closest black pixel. The foreground is obtained by 
applying a threshold on values we get by applying Distance Transform. We simply apply this 
background mask to the segmented image to get our final segmented image.


## References
[P. Felzenszwalb, D. Huttenloche. Efficient Graph-Based Image Segmentation. *Intl Journal of 
Computer Vision*, 2004, 59 (2)]((https://link.springer.com/article/10.1023/B:VISI.0000022288.19776.77))
