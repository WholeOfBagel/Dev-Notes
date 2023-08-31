### Single-view ambiguity
-> stereo: 2 calibrated cameras of different views/correspondenses solving for X
* resolving single-view ambiguity: motion know how moved and calibrate X
* knowing R, t (rotation/translaiton) of camera
* claibration finding out intrinsics of k
* know x,y,z and u,v -> eqs to contraing M 3x4
	* knownd 2d image coords (pixels)
	* known 3d location (measurements)
	* p = $\lambda MX$
	* cross product orthogonal to x,y
* ![[Pasted image 20230308071721.png]]
* p x MX = 0, M has 11 degrees of freedom
* ![[Pasted image 20230308072151.png]]
* QR - decomposition of 3x3 matrix -> finite options of upper tri matrix * rotation
	* to find $K_{3x3}[R_{3x3}, t_{3x1}]$
* overconstrained MX-> not perfect equality
	* parameters with linear model
* ![[Pasted image 20230308072654.png]]
	* can add radial distoration now
* ![[Pasted image 20230308072940.png]]
	* X is only unknown 
*  calibration -> solve M, triangulation -> solve X

