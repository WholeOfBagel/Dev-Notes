
### Connections
Can make a [[Callbacks]] to help track and dynamically change the learning rate,
```python
# Set the learning rate scheduler
lr_schedule = [[tf.keras.callbacks.LearningRateScheduler]](
    lambda epoch: 1e-8 * 10**(epoch / 20))
```


#### Choosing optimal l_r:
###### code
```python
# Define the learning rate array
lrs = 1e-8 * (10 ** (np.arange(100) / 20))

# Set the figure size
plt.figure(figsize=(10, 6))

# Set the grid
plt.grid(True)

# Plot the loss in log scale
plt.semilogx(lrs, history.history["loss"])

# Increase the tickmarks size
plt.tick_params('both', length=10, width=1, which='both')

# Set the plot boundaries
plt.axis([1e-8, 1e-3, 0, 300])
```
###### graph

![[Pasted image 20230906185616.png|500]]
you want to choose the area where it is still stable but relatively minimal for loss
