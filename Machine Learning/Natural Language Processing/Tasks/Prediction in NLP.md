Making use of pad_sequences we can do the following, where the last entry represents the full sentence:
![[Pasted image 20230905160526.png]]

Yet, we would still one-hot encode our labels because this does end up being a [[Categorization in NLP]] problem.

### N-grams
```python
# Initialize the sequences list
input_sequences = []

# Loop over every line
for line in corpus:

	# Tokenize the current line
	token_list = tokenizer.texts_to_sequences([line])[0]

	# Loop over the line several times to generate the subphrases
	for i in range(1, len(token_list)):
		
		# Generate the subphrase
		n_gram_sequence = token_list[:i+1]

		# Append the subphrase to the sequences list
		input_sequences.append(n_gram_sequence)

# Get the length of the longest line
max_sequence_len = max([len(x) for x in input_sequences])

# Pad all sequences
input_sequences = np.array(pad_sequences(input_sequences, maxlen=max_sequence_len, padding='pre'))

# Create inputs and label by splitting the last token in the subphrases
xs, labels = input_sequences[:,:-1],input_sequences[:,-1]

# Convert the label into one-hot arrays
ys = [[tf.keras.utils.to_categorical]](labels, num_classes=total_words)
```
### Simple one-hot model:
```python
from tensorflow.keras.optimizers import Adam

model.add(Embedding(total_words, 100, input_length=max_sequence_len - 1)),

model.add(Bidirectional(LSTM(200))),

model.add(Dense(total_words, activation='softmax'))

# Compile the model

model.compile(loss='categorical_crossentropy',

optimizer=Adam(learning_rate=.01),

metrics=['accuracy'])
```
### Prediction from a model
```python
# Define seed text
seed_text = "help me obi-wan kinobi youre my only hope"

# Define total words to predict
next_words = 100

# Loop until desired length is reached
for _ in range(next_words):

	# Convert the seed text to a token sequence
	token_list = tokenizer.texts_to_sequences([seed_text])[0]

	# Pad the sequence
	token_list = pad_sequences([token_list], maxlen=max_sequence_len-1, padding='pre')
	
	# Feed to the model and get the probabilities for each index
	probabilities = model.predict(token_list, verbose=0)

	# Get the index with the highest probability
	predicted = np.argmax(probabilities, axis=-1)[0]

	# Ignore if index is 0 because that is just the padding.
	if predicted != 0:
		
		# Look up the word associated with the index. 
		output_word = tokenizer.index_word[predicted]

		# Combine with the seed text
		seed_text += " " + output_word

# Print the result	
print(seed_text)
```
