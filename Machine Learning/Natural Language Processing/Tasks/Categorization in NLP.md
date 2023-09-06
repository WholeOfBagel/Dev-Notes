### Going into our dense layers
We do this once we reach our DNN, since our [[word embedding]] is most likely vectorized we need to Flatten() it as we do with images in our convolutional neural networks. 

Alternatively, we can do a one dimensional pulling tf.keras.layer.GlobalAveragePooling1D():
![[Pasted image 20230901145014.png|200]]

#### Comparison
![[Pasted image 20230901145120.png]]
* Flatten() tends to be more accurate, but at the cost of some time