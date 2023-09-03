t### Tokenizer
#### Instantiating Object
###### num_words
the num_words parameter can be set for a larger or shorter value than we actually have in our text. It will sort all the words by volume to make the determination of what remains

###### oov_token
this is what will replace those words which we have never seen (i.e not located within the word index) with this token as a the key
#### fit_on_texts method
is the method we pass our sentences into for tokenization
* this will filter out punctuation
* is case insensitive 'i' and 'I' will be the same

#### texts_to_sequences method
This will give us the different sentences encoded into their values (integers)
1. it will encode any sentence based on what it learned from fit_on_texts
2. it will lose any word that was not found from fit_on_texts

#### word_index property
* returns a dictionary of key value pairs
	key is the word, value is its encoding
* Will always return the full dictionary of words despite the max_len from instantiation

#### index_word property
This is a reverse of the word_index property used for look up contexts

