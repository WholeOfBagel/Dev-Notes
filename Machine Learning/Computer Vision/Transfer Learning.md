Typically we are using a previous model (trained on more data) to use their convolutional layers for the extraction of features from our data. Then we use our own dense layer to make the final assessment on class type.
* you might need to retrain some of the lower convolutions if they are too specific for the application


Our validation accuracy can diverge from our training; thus we can use regularizers like dropoput

### My experience - protocol:
``` python
InceptionV3(input_shape = (150, 150, 3), 
			include_top = False, 
			weights = None)
```
1.  in preparing the input to the model, you want to fetch the pretrained weights of the model and remove the fully connected layer at the end 
	1. we will replace this with our own
2. You will also specify the input shape that your model will accept. 
3. Load the weights: `pre_trained_model.load_weights(local_weights_file)`
4. Want to freeze the weights of these layers because they have been trained already.
	```python
	for layer in pre_trained_model.layers:
	  layer.trainable = False
	```
