Interest points: Harris
Local features: SIFT

* associate pateches with object of interest
* frames of a single shot, faces, background vs what is moving
Gestalt: symmetry, similarity, common fate (coherent motion), proximity, subjective contors (why shape exists)
* whole is other than sum of its parts

### segmentation: separate into coherent objects
* top down: pixels same object -> group 
* bot up: pixels look similar -> group
* superpixels: similar looking pixels

### Clustering algorithms
i. want to find centers 
* minimize SSD between all points in cluster
ii. methods
* k means: randomly initilize k clusters -> for each point find closet c -> given points avg for c -> if c changed iterate again (without random)
	* gives local min (converges reasonably in time), sensitive to start/#initial clusters/must cluster all points(outliers suck), detects spherical clusters
* Feature space
	* intensity+position or color
*  normalzied cuts: have similar appearance forming parts of an object
	* build graph node for every pixel -> every edge has weight which is similarity (affinity) -
	* pic:
		* ![[Pasted image 20230306185631.png]]
		* ![[Pasted image 20230306190043.png]]
	*  exp((-1/(2sigma^2) * ||xi - xj||^2)
	* delete links that cross btw segments
		* cut low affinities
		* min cut (summing up all the weights taht you cut) - removal makes graph disconnected
	* generalized eigenvalue problem
	* pro: does not require model fo data distribution, flexible choice of affinities
	* cons: comp high, dense, preference fore balanced partitions (equal weights - or else could favor really small clutsters ex: small object on big background)