#### range(len)
of course will make a dataset within the range specified 

#### window()
This is called windowing and you can use that with the [window()](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fwww.tensorflow.org%2Fapi_docs%2Fpython%2Ftf%2Fdata%2FDataset%23window) method.
* each window returned is a [Dataset](https://colab.research.google.com/corgiredirector?site=https%3A%2F%2Fwww.tensorflow.org%2Fguide%2Fdata%23dataset_structure) in itself. 
	* This is a Python iterable 
	* as of the current version (TF 2.8), it won't show the elements if you use the `print()` method on it.
##### size
Here, you will take elements per window (i.e. `size` parameter) 

##### shift
can move this window shift elements at a time (i.e. `shift` parameter).


#### drop_remainder
boolean if set to true it will remove sets that are not full sized

#### flat_map()
used to flatten windows and the like into a single dataset
ex: `flat_map(lambda window: window.batch(5))`


#### map()
applies a lambda to every element of the dataset and returns a dataset

#### shuffle()
The `buffer_size` parameter is required for that and as mentioned in the doc, you should put a number equal or greater than the total number of elements for better shuffling.

#### batch()
batching windows/components of dataset

#### prefetch()
optimization

#### take
will grab a single batch

#### from_tensor_slices()