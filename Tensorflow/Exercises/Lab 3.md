### EXERCISES

1. Try editing the convolutions. Change the 32s to either 16 or 64. What impact will this have on accuracy and/or training time.
    
2. Remove the final Convolution. What impact will this have on accuracy or training time?
I believe this will remove a layer os interpretation from the model thereby decreasing accuracy
    
3. How about adding more Convolutions? What impact do you think this will have? Experiment with it.
we actually slightly decrease our accuracy for the training data but our validation remains mostly the same - if we are using 32
```python
# Seeing improvements with the following
class myCallback(tf.keras.callbacks.Callback):
  def on_epoch_end(self, epoch, logs={}):
    if logs.get('accuracy') < .9 and epoch == 3:
      print('this is poop')
      self.model.stop_training = True
callbacks = myCallback()

# Define the model
model = tf.keras.models.Sequential([
                                                         
  # Add convolutions and max pooling
  tf.keras.layers.Conv2D(32, (3,3), activation='relu', input_shape=(28, 28, 1)),
  tf.keras.layers.Conv2D(32, (3,3), activation='relu', input_shape=(28, 28, 1)),
  tf.keras.layers.MaxPooling2D(2, 2),
  tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
  tf.keras.layers.Conv2D(64, (3,3), activation='relu'),
  tf.keras.layers.MaxPooling2D(2,2),

  # Add the same layers as before
  tf.keras.layers.Flatten(),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dense(10, activation='softmax')
])

# Print the model summary
model.summary()

# Use same settings
model.compile([[optimizer]]='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

# Train the model
print(f'\nMODEL TRAINING:')
model.fit(training_images, training_labels, epochs=5, callbacks=[callbacks])

# Evaluate on the test set
print(f'\nMODEL EVALUATION:')
test_loss = model.evaluate(test_images, test_labels)

```
Training Acc -> 93, Validation -> 91 (1% increase on both)
    
4. Remove all Convolutions but the first. What impact do you think this will have? Experiment with it.
The model is going to suck

1. In the previous lesson you implemented a callback to check on the loss function and to cancel training once it hit a certain amount. See if you can implement that here.
Hey I was miles ahead of your, already did that. [[Callbacks]]