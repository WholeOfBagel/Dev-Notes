# Covolutional NN 2
###### Sizing
**binary classification which image is cat** f=1
**multiclassification**: which of 1000 is it F=1000
**Pose recognition**: identify the x,y coord of 28 body joins of human F=56
Generic regression: at what gps cood img taken f2
HxWxC -> 1x1xF # can do avg pool HxW filter s=1
* if F == C 
or HW convo with F filters
###### Alexnet each block is HxWxC
transform one vol to anothe rwith conv
![[Pasted image 20230416204052.png]]
![[Pasted image 20230416204639.png]]
227x227x3 -> 55x55 96 <-decided
11x11 filter stride of 4 (227 - 11)/4 + 1 = 55
para 96 11x11 on 3 + 96
non-linearity applied to every element (sam dims)
conv 1 filters: 3 input dim R,G,B -> 96 filters with random weights (visual filters it found useful)
**For later [[layers]]** take slices differing btw images - compare where high activation appears
![[Pasted image 20230416205602.png]]
filter receptive field - when reach intermediate node what has been touched in the forward
**Classic vs Deep recognition** cut off last linear layer from perlearned model (useful for little data)
as a fixed feature extracter like we did with SIFT -> BOW -> classifier (classic steps don't talk)
###### VGG model 3x3 filters
3x3 followed by 3x3 filter -> filter with 5x5 receptive field
* very local, very few parameters
![[Pasted image 20230416210832.png]]
Can add non-linearities in between each 3x3 filter
![[Pasted image 20230416211518.png]]
backprop leverages chain rule (need to compute all local derivatives and multiply them)
* the deeper it is the multiplication gets closer and closer to 0 (d^(n-1)) is the vanishing gradient
* d >> 1 big -> exploding gradients