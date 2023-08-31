# Gradient Decent
Add regularization to objective that prefers solution:
want accurate model (low loss) but not too complex (low regularization)
###### Optimization 
![[Pasted image 20230416133832.png|400]]
###### Option num 1a grid search
evaluate loss fucntion by sampling space
partition space and pick one that minimized loss:
best, bestscore: none, inf
```
for dim1Value in dim1Values:
	.. 
	for dimNvlaue in dimN vlaues
		w = [dim1value, ..., dimNvalue]
		if L(w) < bestScore
			best, bestScore = w,L(w)
```
scales poorly on high deminesions complex samples perdim^numberofdims
###### Option 1b random search
learn with random points RANSAC style
```
for iter in range(numiterations):
	w = random(N,1) #sample
	score = L(w) #eval
		if score < bestScore
```
slow - throwing darts at high dim dart board can miss
P(all correct) = numgood^N
**Option 1a&1b** sma dim, space bound, obj can't be analyzed otherwise use gradient
###### Gradient arrows rep direction, len mag
rescale to unit length 
![[Pasted image 20230416150014.png]]
Method: move in direction of negative gradient (alpha is the size of this step)
![[Pasted image 20230416150134.png|400]]
###### Computing Gradient
![[Pasted image 20230416150511.png]]
function evals per dimension -> 2
or use calculus - take derivative of L(w)
![[Pasted image 20230416150754.png]]
 Before:  w^Tx. After: $(w + \alpha x)^{Tx}= w^{Tx}+ \alpha x^{T}x$
 abs(x) = ![[Pasted image 20230416151031.png|200]]![[Pasted image 20230416151240.png]]
**Option 1** gradient descent compute over all data
```
for iter in range(numiters):
	g = gradient(data, L)
	w = w + -stepsize(iter)*g #update w
```
**Option 2** stochastic gradient descent over 1 random
```
for iter in range(numIters):
	index = randit(0, #data)
	g = gradient(data[index], L)
	w = w + -stepsize(iter) * g #update 2
```
**Option 3** minibatch gradient descent over subset of b
```
for iter in range(numIters):
	subset = choose_samples(#data, B)
	g = gradient(data[subset], L)
	w = w + -stepsize(iter) * g #update 2
```
Learning rate i.e. stepsize (lower it over time - don't overshoot later)
Solution avergate gradient: exponentially decaying weights: called momentum
###### Optimize
w on training set with SGD to max training acc
$\lambda$ on random/grid search to max validation acc
optimizing $\lambda$ ontraining sets it to 0
bias: error intrinsic to model
overfit: taking every datapoint too seriously
* high variance - removing one var changes
* 
underfit: too little parameters to represent features
big weights = more complex model
fitting:
![[Pasted image 20230416152650.png]]
no reg: fits all datat points, reg: can't fit all