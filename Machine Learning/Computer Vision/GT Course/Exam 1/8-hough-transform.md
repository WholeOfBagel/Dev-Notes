### Line fitting
* why fit lines: many objects characterized by presence of straight lines
* problem: extra edge points clutter it, missing lines, noise in edge points

### Voting
* all local features vote for all models compatible with it (look at parameters with lots of votes) - noise will make votes but will be as outlier
	* for every edge point
* look for lines that get many votes

Process:
* y=mx + b -> point based on parameters m and b
* point in x,y -> b = -xm + y (line in hough space)
* intersection of lines in hough space = line that passes through two coordinates in image space -> quantize and bin each grid spot for votes
* polar representation: 
	* ![[Pasted image 20230307123304.png]]*$xcos(\theta) + ysin(\theta) = d$
* point in img -> sinusoid segment in hough
### Algorithm
1. $H[d, (\theta)] = 0$$
2. for each edge point I[x,y] 
	1. for theta = $[\theta_{min} to \theta_{max}]$
	2. ==theta = graident at x,y==
	3. $xcos(\theta) + ysin(\theta) = d$
	4. $H[d, (\theta)] += 1$
3. find (d, theta) where H[] is max
4. detect line given by d

### Tuning
* same d and theta can't vote for multiple lines
* still see peaks in noise voting space -> gradients & orientation
	* or give more votes to stronger edges 
	* or smapling of d, theta to give more or less res
* $$(x_i - a)^2 + (y_i -b)^2 = r^2$$
	*  now cirlces instead of lines intersecting -> intersecting circles centered at points of hough space -> on edges of circle in img
	* unknown radius = cone in hough space
		* can use gradient angle of img space -> hough space line ray
	* for circle:
		* ![[Pasted image 20230307125546.png]]
	* minimize irrleavant tokens first
	* choose a good grid/ discretization
		* too fine<---->too course
		* voting for nearby (smoothing in acc array)
	* use direciton of edge to reduce para by 1
* Pros: all points are processed ind, don't need all points on line, noise points unlikely to contribute big to bin, detect multiple instances of a model in single pass
* Cons: more complex shapes for each parameter, non-target shapes offset, quantizations of grid need to bet specified

### Generalized (for arbitrary shapes)
* ex: 
	* ![[Pasted image 20230307130244.png]]
* offline procedure: at each boundary point find r = a - p_{i} a is potential center, r vote
	* dispaclement vectors in table indexed by gradient orientation
	* look for overlaps in r
* not rotation invariant