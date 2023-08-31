Recognition:
* Local features: visual words
* Full image features: bag of visual words
Matching
* feature similarities: local or full
* inverted file index efficient search
* spatial verification: spatial correspondences compute homography
Linear Model because we cannot directly compute the homographies for class models need learning:
* model types: linear regression, softmax, kNN
* tech: data separation, regularization, hyper fitting
fixing overfitting: increase data, decrease params, add regularization or increase loss of regularizor
**Visual words** 
find? kmeans clustering
* words are cluster centers
new image has features -> what would BoW be?
* BoW is histogram of each w `[count1, count2]`
###### Classifiers
k=1 means you just take the max
k=3 means you assign the majority
* if all are tie -> has no answer
binary affine: 2 weights, 1 bias
20 dim, 5 classes -> 20x5 + 5 params
###### SGD
algo: walk along negative gradient
params: step-size/learnign rate, [[Batch]] size
* leanring rate too large (can miss minima)
* too small: get stuck on local
regulizers: momentum, weight-decay
**Neural Nets**
* linear/full connected blocks
* activation functions add non-linearity
df/dq was in between blocks
###### Covnets
* conv vs linear layers: computing block sizes, para
	* conv allows us to go deeper by reducing par
* function to apply to parameters:
	* 100x100 input, 5 nodes -> 100^2 x5 + 5
	* filter size 5x5 5 filters -> 4x4x5 + 5 
* conv layer stride 2 (100-4)/2 + 1
* Modeling tools: 3x3 conv, [[Batch]] normalization, data aug, fine tuning
* semantic segmentation: unpooling transpose conv
* 

