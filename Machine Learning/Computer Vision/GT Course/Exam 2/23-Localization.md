# Localization
###### sol1 [[Batch]] Normalization in btw layers
normalizes activates into normal distribution
![[Pasted image 20230416212046.png]]
if values varry a lot -> gradients becom huge
too compact -> gradient too small
(want right img), subtract out emperical mean
gradient values stay closer to 1
###### Residual Learning
new building block: x + F(x)
![[Pasted image 20230416213023.png]]
skip connections: allowing model to decide what extra stuff it might want to add vs having to always pass through
###### Training CNN
```
1. download big dataset
2. initialize network weightrs randomly
3. for epoch in rang
	1. shuffle dataset
	2. for each minibatch in dataset
		1. put dat on gpu
		2. compute gradient
		3. update gradient with SGD
```
![[Pasted image 20230416213656.png]]
###### Trainig covnet
fewer data points that parameters = trouble
solution: need regularization/more data, agumentation that don't affect output
**Fine tuning** initialize the weights with one that has already been made from existing network
* few images: don't use fine tuning <10k
	* fixed feature extraction and linear cut off
* 10k<medium<100k try fine tuning
* 100k < consider trying from scratch
###### Localization vector output per pixel
HxW image into HxWxF (needed for semantic)
* don't distinguish between object instances!
* could be naming things
![[Pasted image 20230416214915.png]]
need HxW losses for the entire image instead of 1
* could make a depth map (regression)
###### Encoder-Decoder
![[Pasted image 20230416215123.png]]
larger -> smaller is encoder 
smaller -> larger is decoder
map 1x1xC -> 1x1xF need matrix that is CxF
* W(FxC matrix) + b (Fx1 vector)
with convolution filter of size 1x1 with F filters
![[Pasted image 20230416215310.png]]
linear layer -> convolutional (could have image that is x4 in size -> apply alexnet) less restricted by size
**upsampling** opposite downsampling by unpooling
convolution -> transpose convolutoin
* nearest neighbor [[Pooling]] operation like reverse of max pool -> recover size that we previous had
* add padding around or padding in between each element
**Accuracy** intersection over union, avg over classes





