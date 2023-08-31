df/dx high change means vertical edge

#### Looking for edges graph
![[Pasted image 20230306111323.png]]

#### Gaussian
Gaussian derivative (speed things up):
* don't have to differentiate whole thing -diff gausssian * f
* x high -> low
* y low -> high 
Take laplacian of gaussian (2nd derivative - zero crossing)
![[Pasted image 20230306112134.png]]
* more sigma smooths it out over wider -> less edges in more detailed areas
### Detection
##### detection
1. smoothing
2. edge enhancement
1&2 can be done through derivative of gaussian

### Canny edge detection
3. edge localization (threshold) -> binary image
	1. pixel less than t set to 0
	2. others to 1
* non max suppression edge width-> single pixel 
	* specific location by gradient direction
* low and high threshold (high starts low finishes edge curves)
Derivatives
* smoothing _negative signs_ used to get high response in regions of high contrast
* sum to 0 -> no response in constant regions
* high abs at points of high contrast

### seams
edge strength = gradient magnitude
* choose min seam
![[Pasted image 20230306120443.png]]