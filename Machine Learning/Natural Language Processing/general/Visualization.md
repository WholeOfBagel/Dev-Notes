## Embedding Projector
The prime example I have seen is tensorflow's [Embedding Projector](https://projector.tensorflow.org/) this will reduce the 3+ dimensional word embeddings into a 3D system with poles that will represent the opposing sentiments

### Example
```python
# Get the embedding layer from the model (i.e. first layer)
embedding_layer = model.layers[0]

# Get the weights of the embedding layer
embedding_weights = embedding_layer.get_weights()[0]

# Print the shape. Expected is (vocab_size, embedding_dim)
print(embedding_weights.shape) 
```
You will need to generate:
- `vecs.tsv` - contains the vector weights of each word in the vocabulary
- `meta.tsv` - contains the words in the vocabulary
- `reverse_word_index` dictionary so you can quickly lookup a word based on a given index.
	- this can be done through the word_index property on tokenizer

``` python
import io

# Open writeable files
out_v = io.open('vecs.tsv', 'w', encoding='utf-8')
out_m = io.open('meta.tsv', 'w', encoding='utf-8')

# Initialize the loop. Start counting at `1` because `0` is just for the padding
for word_num in range(1, vocab_size):

  # Get the word associated at the current index
  word_name = reverse_word_index[word_num]

  # Get the embedding weights associated with the current index
  word_embedding = embedding_weights[word_num]

  # Write the word name
  out_m.write(word_name + "\n")

  # Write the word embedding
  out_v.write('\t'.join([str(x) for x in word_embedding]) + "\n")

# Close the files
out_v.close()
out_m.close()
```