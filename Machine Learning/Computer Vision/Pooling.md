Pooling is used to compress. We have to be mindful of the edges.
- ex: if we have a 3x3 filter we will have -2 on x and -2 on y for the dimensions for convolutions
	- -> 5x5 4 smaller & 4 smaller
- 2x2 pooling -> halving (rounding down)

#### Helpful Diagram
![[Pasted image 20230802221720.png]]
![[Pasted image 20230801180259.png]]

### Types of Pooling
* Max pool: take highest from window
* Avg pool: take avg over window for out

### Code
[[tf.keras.layers.MaxPooling2d]]
This is used as a layer in a conv2d
