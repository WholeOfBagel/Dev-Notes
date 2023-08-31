Pridicting transformed image from T and og img
Projective transformations:
* matrix
	* ![[Pasted image 20230307155515.png]]
* parallel lines -> not nec parallel

### fitting 2d transformation

Image reprojection:
* Pinhole camera -> different camera views to projection plane
* rectangle can map to arb quad
* parallel aren't preseved but must preserve straight
* unique up to scale factor -> constrain Frobenius norm of H to be 1 (single homo)
* 3x3, 8 free variables bc of scalar -> 2 eq per correspondence
	* ![[Pasted image 20230307160019.png]]
	* h are unknowns (h1 is row)
* equations: $x' = \frac{h_1^tp}{h_3^tp}$
* minimize: $x' -> h_1^tp - x' (h_3^tp) = 0$
* L = ![[Pasted image 20230307161104.png]]
* $min({h^{t}A h})$ s.t. $||h||^{2}= 1$
	* smallest eigenvalue solves

### 2d image warping
* can't convert directly to pixel lcoation
	* lies btw two pixels -> distribute color amongst neighbor (splatting)
		* a lot of blur
* inverse warping $(x,y) = T^{-1}(x', y')$
	* btw: bilinear in 2d a,b distance is weight to the four points

### Computing Mosaic
1. take sequnce of images form same pos
	1. rotate camera around center
2. compute transformations
3. transform second image to overlap with first
4. blend two

* known shape -> some view (image rectification)

Changing camera center

RANSAC for estimating homography
1. select four feature pairs (at random)
2. computer homography H (exact)
3. compute inliers where SSD (pi, Hpi) < small
4. keep largest set of inliers
5. recompute ls H estimate on all of inliers