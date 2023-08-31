photometric: type, direction, intensity of light, surfaces reflectance property
optical: focal length, fov, aperture, shutter speed

### PInhole camera model
* image formation
	* every point on a tree blends its colors all across the film
	* -> barrier known as aperture (only one makes it through) flipped
	* f = focal length, c = center of camera
		* f distance from pinhole and img
	* lines all to vanishing point
* facts about projection
	* line in 3d -> line in 3d
	* parallel 3d -> loses, but converge to central point
	* distant objects are smaller
* increase aperture (when too dark)

### projective geometry
* structure
* 2 vanishing points < img -> vanishing line
	* might not all perfectly intersect
	* minimize angular differences
* triangles: ![[Pasted image 20230307213540.png|300]]
* ![[Pasted image 20230307213846.png|500]]
* 
### projection matrix
$K[R t ]X$
* ![[Pasted image 20230307214013.png|300]]
* extrinsic ass: no rotation, camera at 000 4th col
* intrinsic ass: opticalcenter000,unit aspe,!skew
* rotations: ![[Pasted image 20230307214346.png]]
* ![[Pasted image 20230307214524.png]]
* focal length on left, u0v0 optical center, rotation, translation, 3d point
