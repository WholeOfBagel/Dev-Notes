Intuition: Can't rely on any one feature -> have to spread out weights.
* neurons can potentially affect neighbors too much so we want to minimize that
	* happens when neurons have similar weights
* similar effect as [[L2 regularization (ridge)]]

We can apply different probabilities to different layers 
* For layers that we are less concerned about overfitting for we can apply higher probabilities to keep


### Downsides
* Hard to define the cost function - harder to calculate and debug
	* might have to turn off dropout if you want to make sure your cost function is being handled properly across the iterations