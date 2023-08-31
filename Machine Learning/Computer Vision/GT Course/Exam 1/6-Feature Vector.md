### Lin Alg
* old*
	* linear independence
	* span: all linear combiantions of set of vectors
	* Ax output is constrained to span of cols of A
	* full rank: one-to-one mapping -> invertible
* Symmetric $A= X^{T}X$ 
* rotation matrix: all row/col have l2 norm, lin ind, transpose is inverse, det = 1, eigenvlaue = 1
* eigensystems: lagest eigenvector = vector with largest value

### Description
* Approximating Laplacian
	* *![[Pasted image 20230306181248.png]]

trying to do multiple scales
* simple descriptors: raw pixel vectorized (highly sensitive to noise/shifintg) -> SIFT
* Histograms to bin pixels sub-patches accoridng to thier graident orientation (don't vectorize)
	* mag: old determines weight of histo
	* angle: tan
* compute histograms for different patches

Oreint patch by max weight and make this the 0
* less bins -> less orientations = less info
* more bins -> too much info

partially invariant to
* illumination changes
* camera viewpoint
* clutter

### Matching
* find patches that have most similar (lowest SSD)
	* **(Xi – Xj)2 + (Yi – Yj)2** for every distinct pair **(i, j)**
* robustness: distance to best match/distance to second best match 
	* =1 is ambiguous
	* lowest: first match looks good
* 

* hypothesize tranformation -> apply trans and see if more match