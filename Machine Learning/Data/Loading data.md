```
# Get current working directory
current_dir = os.getcwd()

# Append data/mnist.npz to the previous path to get the full path
data_path = os.path.join(current_dir, "data/mnist.npz")

# Discard test set
(x_train, y_train), (x_test, y_test) = tf.keras.datasets.mnist.load_data(path=data_path)
        
```

`flow_from_directory` method for ImageDataGenerators