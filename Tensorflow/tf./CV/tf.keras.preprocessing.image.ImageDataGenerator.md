
### Uses
* ImageDataGenerator instantiation
* train_datagen.flow_from_directory() to get the generator object
	* points to train_dir

### Tips
* do not point it at the subdirectory, you have to 
* need to resize all the images to be the same size
	* the advantage of using ImageDataGenerator is that you get to do the resizing at runtime -> can experiment 
* [[Batch]] Size is defined here

