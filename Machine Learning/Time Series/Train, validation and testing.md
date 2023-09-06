### Fixed Partitioning
![[Pasted image 20230906151533.png]]

* have to be aware of seasonal data:
	* want equal representations of each month (if it is monthly) so choosing whole values in that respect is important
* incorporating more data (once we get to a healthy point)
	* once we are getting good results on validation we can add the validation to the training then we can test it with the test period
		* after this we can train using the test data

### Roll-Forward Partitioning
![[Pasted image 20230906152037.png]]
we are training on ever increasing periods and testing that period (day, week, month) on the validation