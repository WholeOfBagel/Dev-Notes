* F is estimate known as weak calibration
* E = ![[Pasted image 20230308084216.png|100]]
* from E calc relative rotation/translation
* scene point z direction
* disparity: x - x', inveresly proportional to depth
For each pixel
1. find coreresponding ep line in right
2. search along and find best match (SSD)
3. tri matches to get depth
![[Pasted image 20230308084853.png|500]]
y points are the same
Stereo image rectificiation
* create virtual planes that only differ by translation
* -> pixel motion is horiz -> 2 homo for each img
* distance min, similarity max
	* sum(l - r)^2 vs 

Triangulation
![[Pasted image 20230308085826.png|300]]
z = B*f/(z-x')


