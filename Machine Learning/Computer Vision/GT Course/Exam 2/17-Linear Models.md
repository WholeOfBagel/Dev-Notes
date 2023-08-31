# Linear Models
Objective function: can be min/maxed as a goal
you fit/learn T using: 
* pairs of data points (x data, y desired)
* just using set of datapoints x (need to define y)
x: feature vector/data point dead dim or feature is some aspect of this data 
y: label/target each dimension represents some aspect of output data
maping to continuous, capture variance of data PCA
Bag of words gives us a better input
| | supervised                   | unsupervised |
| ----- | ---------------------------- | ------------ |
|d |classfication/categorization | clustering              |
|c |regression (weight)                   | dim reduciton              |
N eqns > N vars -> overdetermined (will have errors)
N eqns = N vars -> exact solution
N eq < N vars -> undertetermined (infinite solns)
model: y = mx+b or y = w^Tx
obj function: 
-> $\sum^{k}_{i=1}(y_{i}- w^{T}x_{i})^{2}$ $||y - Xw||^{2}_{2}$
![[Pasted image 20230415222132.png|250]]
loss function evaluates correctness: argmin on L2 norm or SSE
training/learning/fit minimizes this closed for SSE: $w^{*} = (X^TX)^{-1}X^Ty$
inference(x) = $W^{Tx}= w_1x_{1} + w_nx_{n}$
###### Separated Testing
[[Overfitting]]: fitting datapoints too strictly poor on fin
* num datapionts = params = perfect fit
lat, high, snowfall -> nx4 x matrix
linear regression for predicting temperature
**Rank deficiency** more features than dim n -> no inverse -> infinite number of solutions -> regularization
![[Pasted image 20230415223529.png|300]]
![[Pasted image 20230415223618.png|250]]
$\lambda$ is a hyperparameter which we have to provide
0 -> least squares; $\infty$ -> w = 0;  need-> validation
![[Pasted image 20230415223927.png|300]]![[Pasted image 20230415224156.png|150]]
![[Pasted image 20230415225032.png|400]]
![[Pasted image 20230415224429.png|400]]
as num data -> $\infty$ error rate is gauranteed to be at least x2 worse than optimal (since we not learning)
**Linear model** 1 weight per class 
$W_{CxF}$ classes x features
###### Geometric Intuition
close to line distance from boundary gets smaller
if wi is big -> values of xi are indicative
**Multiclass SVM** - minimize [[Overfitting]] to objective
![[Pasted image 20230415230300.png]]
first Wxi is incorrect class and second is based off correct, so we want prediction for correct to be big
**Objective 2 [[Softmax]]** making probabilities
e^x -> sum used to normalize vector for out
![[Pasted image 20230415230737.png]]
![[Pasted image 20230415230844.png]]
p(corrrect) = 0 -> infinite penalty for neg log
p(correct) = 1 -> no penalty for neg log likelihood

