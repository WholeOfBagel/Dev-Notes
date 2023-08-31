# Instance Recognition
* visualize words: quantization, index, bag of word
* spacial verification: affine, ransac, hough
* Query/organize data by finding similarity btw scenes
	* instance means object vs category recognition
1. interest point detectors used like:
	1. harris (invariant to trans rotation illumination)
	2. or sift (rotation invariant, scale invariant)
2. regions that we find interesting -> extract as vector
3. lowest SSD (compare all and take closest within d)
**Using Stereo** disparity how far pixel moved in x and y
-> define box that we can search in
**Indexing local features** boxes contribute feature v
* which building corresponds? look through features
-> don't compare each: **visual word**/descriptor
* exists as point in high dimmension space
* assumption **close*** is more similar
* input query and find **closest**
* **Challenges**: Scale, efficiency in finding
**Inverted file index**: what page the things show up on
* find all images=page in which feature=thing shows
###### Visual Words
texton: cluster centers of filter responses over images
simple d/dx dim1; d/dy dim2
1. extract features -> point on dimmensional on plot
2. partition: reducing search (kmeans) center=vw
3. Inverted file index Word | Image 
	* find word -> consider img
**Issues**: sampling where?, clustering, supervised?, universal vocab?, vocab size/num words?
* every pixel sampling = not informing (hard matching)
* little clusters means more searching
###### Summary via bag of words
Histogram over wordcounts (wordcount for vw)
* categorize each image with histogram of words
* rank frames by normalized scalar product of counts
	* could be weighted -> nearest neighbor search
* index of indiviudal words
**Pro** compactness, vector representations, results 
* flexible to geometry/deformation/viewpoint bc hist
**Cons** geo, background, optimal formation clarity
* ignores geometry, must verify afterwards, encode fea
* background and foreground mixed (whole img bag)
* optimal vocabulary formation remains unclear
###### Retrieval quality, PR curve, optimize
precision = #relevant/#returned //how many are rel
recall = #relevant/#totatl relevant //of rel returned/tot
Avg percision: until we find all return find area under
**vocab size**:How well for each vocab size -  sparsity
**spatial verification**: affine, RANSAC, hough
* similarity btw transformation lines (describe more with single transformations) = RANSAC, hough
**RANSAC** more inliers = better match
* minimum subset of corr to estimate -> inliers
* uncertainty in img space
* must search all data points for inliers
* scales better in high dim
**HOUGH** each matched feature cast a vote on:
* location, scale, orientation of model obj
* uncertainty in parameter space
* linear complexity in corr & voting beyond 4D imp
* handle high outlier ratio
* needs to be invariant for base selection
* verify with enough votes
* gradient orientations all along edge of obj
1. collect all words within query region
2. inverted file index  to find relevant frames
3. compare word counts
4. spacial verification










