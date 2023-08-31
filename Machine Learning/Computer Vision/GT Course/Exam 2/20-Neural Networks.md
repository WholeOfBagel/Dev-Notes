# Neural Networks
1. use linear models for image classfication problems
2. use loss functions to express preference over different choices of weights
3. SGD to minimize loss function and train model
4. Add regularization to control [[Overfitting]]
**mointor learning** error on new data comes from:
* bias: model is oversimplified and cannot fit data
* Variance: you don't have ability to estimate from limited data
* Inherent: the data is intrinsically difficult
Trade off btw bias and variance
![[Pasted image 20230416153732.png]]
small data: inflection closer to y axis -> overfits w/lil
big data: further on x -> overfits with bigger model
**underfitting**: poorly on training + validation with bias
sol: more features, more pow model, reduce regulariza
**[[Overfitting]]**: well on training, bad validation, due to vari
sol: more data, less powerful model, regularize more
generally want to overfit -> then cut down
###### Neural Networks
input image: $x \in R^{D}$category scores: $s \in R^c$ 
![[Pasted image 20230416154529.png]]
max function above is [[Relu]] which is the nonlinearity
* if you remove this collapses into linear
![[Pasted image 20230416154701.png]]
fully connected means: every element each layer con
width size of each layer, depth  = num [[layers]]
deeper: more processsing, less interpretable, [[Overfitting]] with low data, increase complexity
![[Pasted image 20230416155105.png]]
![[Pasted image 20230416155900.png]]
Space warping based off of h = Wx trying to make it linearly seperable - but with non-linearrity 
![[Pasted image 20230416160753.png]]
origional space -> can do linear separation in feature 
