Useful in applications where order of tokens matter in a sequence. Typically very slow.
Values from earlier words can be carried to later ones via a cell state. 

![[Pasted image 20230907174828.png]]

### Birdirectionality
Bidirectional allows LSTMs look forwards and backwards in a sentence
```
tf.keras.layers.Bidirectional(tf.keras.layers.LSTM(lstm_dim)),
```
* Will also double the parameters in the output 64 units -> (None, 128)

### GRU
Alternatively one can use a GRU which is essentially a simpler version of LSTM
![[Pasted image 20230905171915.png]]
