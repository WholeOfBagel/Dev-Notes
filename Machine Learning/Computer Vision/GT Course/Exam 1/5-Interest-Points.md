#hi
### Harris Corner Detection
Need:
* [[repeatability]]: despite geometric transformations - correspondence
* Saliency: small distinctive subset
* compactness/opt: fewer features than pixels
* locality: small area of image (no cluter)

How:
* eigenvalues give us basis vector
	* eigenvalue >> other -> edge
* rotation invariant: by eigen to find new basis rotation
* scale invariant: no -> yes
	* choosing window size: expand radius -> get most activation for each pixel
1. cornerness: M matrix
2. threshhold: keep high
3. local filter for most cornerlike
	1. non-max suppression
Formulas:
R = det(M) - alphatrace(m)^2
	*\R\ small: flat, R > 0: corner,
![[Pasted image 20230306173723.png]]


### Blob destection
* edge = ripple, (2nd of guass) -> blob is is where ripples dip lower
	* mag of laplacian will provide scale of blob - smaller laplacian dip wants smaller blob -> (characteristic scale)