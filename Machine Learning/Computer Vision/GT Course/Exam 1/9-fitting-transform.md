# 2d Transform
* Method: finding correspondences
* transformations: translation, rotation, aspect, affine (change shape), perspective
	* p' = T(p) = Mp
	* when p is in R^2 -> 2x2 M
* uniform scaling: same scalar for all components
* non uniform -> new aspect ratio

#### Matrix
$x' = ax, y' = by$
* ![[Pasted image 20230307132456.png]]
* rotating around 0
	* ![[Pasted image 20230307132539.png]]
* sheer
	* ![[Pasted image 20230307132617.png]]
* mirror about y
	* ![[Pasted image 20230307132643.png]]
* translation
	* not in 2d -> 3x3
### homogenous coordinates
to homo -> x, y, 1
from homo x,y,w -> x/w, y/w
* found in rightmost col with diag 1
* ![[Pasted image 20230307140443.png]]
### Affine Fit
![[Pasted image 20230307140533.png]]
* parellel lines remain parallel
* feature based alignment
* eigenvectors are orthonormal
	* symmetric A eigenvector w largest $\lambda$ max $\frac{x^{t}Ax}{x^{t}x}$ unit vectors max num
* non symmetric -> sVD: U$\sum\limits$VT^
	* u rotation eigenvectors of AA^t
	* $\sigma$ sqrt of A^tA $\lambda's$
* solving least squares invert A find v (m,b) point -> minimizing error
	* by argmin: ![[Pasted image 20230307141820.png]]
	* satisfying: ![[Pasted image 20230307141926.png]]
	* when A is square, rank < rows or rank < cols
	* homo ls -> orthogonal to vectors argmin(||Av||^2) smallest ev from AtA, smallest singular v of A
	* for 2 variables need at least 2 eq
		* ![[Pasted image 20230307142400.png]]

### ransac - reduce noise
* not true matches -> outlier (minimising lq creates error)
	* look for inliers
For N times
1. select random seed group s points
	1. more points = more robust
2. compute transformation for seed group
3. find inliers to this transformation
	1. point whose d is < t
4. if large then recomputer estimate M on all of inliers
	1. d > inliers accept and refit using all inliers