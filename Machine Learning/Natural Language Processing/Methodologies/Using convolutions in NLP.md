This groups together words, but can shave off words from our network's consideration so we do have to be careful.

However you will have to use Conv1D:
```python
tf.keras.layers.Conv1D(filters=filters, kernel_size=kernel_size, activation='relu'),
tf.keras.layers.GlobalMaxPooling1D(), #pairing it with pooling
```

This only affects one dimension in the output (obviously but I missed this originally)
ex: If a sentence has 110 tokens in it, and a Conv1D with 64 filters with a kernal size of 5 then its output shape is None, 106, 64


### Example:
```python
model = tf.keras.Sequential([ 
        # This is how you need to set the Embedding layer when using pre-trained embeddings
        tf.keras.layers.Embedding(vocab_size+1, embedding_dim, input_length=maxlen, weights=[embeddings_matrix], trainable=False),
        tf.keras.layers.Conv1D(kernel_size=2, filters=64, activation='relu'),
        tf.keras.layers.GlobalMaxPooling1D(),
        tf.keras.layers.Dense(6, activation='relu'),
        tf.keras.layers.Dense(1, activation='sigmoid')
    ])
    
    model.compile(loss='binary_crossentropy',
                  optimizer='adam',
                  metrics=['accuracy']) 
```
128 filters, 2x2 convolutions
![[Pasted image 20230905154818.png]]
64 filters, 2x2 convolutions
![[Pasted image 20230905160154.png]]
the final nail in the coffin was to include a dropout:
![[Pasted image 20230905161449.png]]
