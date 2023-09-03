1. we know that encoding every character ignores the semantic structure of words; consequently, we are going to tokenize every word. 
		- This can be done through [[tf.keras.preprocessing.text]]
		- The simplest form of this is simply encoding them as a number, but more formally to create semantic similarity between words we need vectorized encoding - this is called Word Embedding
1. we need a lot of training data precisely because of the limitation of introducing our model to new words it has never experienced
	1. we can simply lose it or replace that novel word
2. we need to have uniformity (padding) with the sequences that we are putting into our models

### Word Embedding
Words that are similar end up having close distances -> words cluster together giving us their sentiments. More detailes on [[Word Embedding]]