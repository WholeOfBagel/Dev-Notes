If we want to stop our model at a certain accuracy this is what we do:

```python
class myCallback(tf.keras.callbacks.Callback):
	def on_epoch_end(self, epoch, logs={}):
		if(logs.get('accuracy') >= 0.6): # Experiment with changing this value
			print("\nReached 60% accuracy so cancelling training!")
			self.model.stop_training = True
callbacks = myCallback()

fmnist = tf.keras.datasets.fashion_mnist
(training_images, training_labels) , (test_images, test_labels) = fmnist.load_data()
training_images=training_images/255.0
test_images=test_images/255.0

model = tf.keras.models.Sequential([
	tf.keras.layers.Flatten(),
	tf.keras.layers.Dense(512, 
	activation=tf.nn.relu),
	tf.keras.layers.Dense(10,
	activation=tf.nn.softmax)
])

model.compile([[optimizer]]='adam', loss='sparse_categorical_crossentropy', metrics=['accuracy'])

model.fit(training_images, training_labels, epochs=5, callbacks=[callbacks])

```