### Basics
#### Code
```python
def moving_average_forecast(series, window_size):
    """Generates a moving average forecast

    Args:
      series (array of float) - contains the values of the time series
      window_size (int) - the number of time steps to compute the average for

    Returns:
      forecast (array of float) - the moving average forecast
    """

    # Initialize a list
    forecast = []

    # Compute the moving average based on the window size
    for time in range(len(series) - window_size):
      forecast.append(series[time:time + window_size].mean())

    # Convert to a numpy array
    forecast = np.array(forecast)

    return forecast
```
#### Direct Simple Example
![[Pasted image 20230906152830.png]]

#### Cons
Helps us remove noise but at the cost of not anticipating [[trend]] or [[Seasonality]]
### Differencing
#### Removing Seasonality + Trend
We remove the seasonality and trend -> "so instead of studying time series itself, we study the difference between the value at time T and the value at an earlier period."

###### Example for yearly differencing
```python
# Subtract the values at t-365 from original series
diff_series = (series[365:] - series[:-365])

# Truncate the first 365 time steps
diff_time = time[365:]

# Plot the results
plot_series(diff_time, diff_series)
```
###### Result

![[Pasted image 20230906153119.png]]
#### Adding back in Seasonality + Trend
```python
# Add the trend and seasonality from the original series
diff_moving_avg_plus_past = series[split_time - 365:-365] + diff_moving_avg

# Plot the results
plot_series(time_valid, (x_valid, diff_moving_avg_plus_past))
```

After calculating the moving average here we can then apply trend and seasonality back into the data - but as you see this also reintroduces noise:
![[Pasted image 20230906153400.png]]

#### Removing the introduced noise
![[Pasted image 20230906153417.png]]

This makes use of a [[Trailing Window]] over the present values