# CovNets

### Structure
forward pass: compute function
backward pass: compute derivate of all parts f
Each hidden layer acts as a hyperplane separating
* derivative of output/error with respect to all w
![[Pasted image 20230416184101.png]]
#### Update Function
```
W = initializeWeights()
for i in range(numiterations):
	#sample a [[batch]] 
	batch = random.subset(0, #datapoints, K)
	batchx, batchy = dataX[batch], datay
	#compute gradent with batch
	gradW = backprop(Loss(NN(batchx, W), batchY)) #computes all gradients
	#update W with gradient step
	W += -stepsize * gradW*
```
Loss tells us how close we got to our desired input
L(n) = Wn + b # W^Tx + b # +/- dist to line
looking at absolute dist from line: $max(w_{1^{t}x}+ b, 0) + max(-w_{1^{t}x}+ b, 0)$
next layer: w_1 distance - w_2 distance > 0
###### Parameters
weigths 1x3 -> parameters 3 (bias is 3rd)
2 x | 4 h | 1 y -> weights 1x4 + 4x2 = 12 -> 12 + 5
number of parameters tells you how many datapoi
![[Pasted image 20230416190401.png]]
-> reduction by convolutional NN
keep spatial resoltuion around
Fx1 transform ma-> HxWxF transform: convolution
![[Pasted image 20230416190627.png]]
h,w is local in space summing over only f_h f_w
while c is global: sum over all channels
![[Pasted image 20230416190918.png]]
height? 32 - 5 + 1 = 28, width? 32 - 5 + 1 = 28, channels? 200 -> 28x28x200

### Comparison with [[20-Neural Networks]]
![[Pasted image 20230416191138.png]]

### Filters & Layer Outputs
Stride: how much are we moving the filter
* add padding to allow for various strides
![[Pasted image 20230416191358.png]]
input: 32x32x3, 5x5 stride 1, neurons 5 28x28x5
num of parameters: (5x5)x3x5 = 380 SIZExCxN
Changing stride only changes output volumn

### other layers - [[Pooling]]
##### Motivation
Want spatial resolution of activation/images smaller; applied per channel
##### Tools
* Max pool: take highest from window
* Avg pool: take avg over window for out

##### Pro/Cons
* Losing spatial specificity, can learn on fewer ex
	* too simple: very little we can learn from it
* But we gain so much in way of reduced space while maintaining core features by pooling


### Implementation
Done through [[tf.keras.layers.Conv2D]] & [[tf.keras.layers.MaxPooling2d]]
* We typically are aiming for 2-3 convolutional layers and then a pooling layer.