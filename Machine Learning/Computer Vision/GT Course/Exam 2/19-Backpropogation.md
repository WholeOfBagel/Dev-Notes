# Backpropagation
want: ![[Pasted image 20230416161720.png|120]] s.t. we can use SGD on complex L(f)
**Chain rule**: ![[Pasted image 20230416162148.png| 150]]
f(x) = (-x + 3)^2
f = q^2, q = r +3, r = -x  indiviudal funcitons -> partial
**Backprop** n -> f -> f(n)        g*(df/dn) <- f <- g
* g=1 if no previous gradients
![[Pasted image 20230416162903.png]]
two inputs: send gradients with respect to each var
![[Pasted image 20230416163606.png]]
![[Pasted image 20230416164430.png]]
![[Pasted image 20230416164545.png]]![[Pasted image 20230416170022.png]]
Sum all of things that backprop returns for the input
![[Pasted image 20230416164926.png]]
= $(1 - \sigma(n)\sigma(n))$
![[Pasted image 20230416165441.png]]
**sigmoid** btw 0 and 1: changes output range
gradient are near 0 if neuron is high/low: can stop learning/dectivate a neuron
**[[Relu]]** constant gradient, converges faster, neg -> 0 g
**leaky [[Relu]]** x if x >= 0 .01x x < 0
###### Fully connected Network
$h_{i} = f(w_{i^T\alpha}+ b_i)$ 
![[Pasted image 20230416182251.png|300]]
