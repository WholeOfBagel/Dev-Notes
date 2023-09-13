
![[Pasted image 20230906152149.png]]
MSE squares errors because a error in the other direction (negative) still should be considered as a error away from what we want.

RMSE: mean of error's calc to be of same scale as og errors then we take sqrt

MAE: uses absolute value instead of squaring negatives, also penalizes big errors less than MSE

MAPE: mean ratio between the absolute error and absolute value: compares size of errors to values

### New Loss Functions
making use of Huber Loss as opposed to mse or mae:
"The squared loss has the disadvantage that it has the tendency to be dominated by outliers—when summing over a set, the sample mean is influenced too much by a few particularly large a-values when the distribution is heavy tailed: in terms of estimation theory, the asymptotic relative efficiency of the mean is poor for heavy-tailed distributions."