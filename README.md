# Day-51---Time-Series-Analysis-with-Pandas
As part of a 75-day data analysis challenge, this work on Python covers time series analysis using Pandas library

## Objective:

To learn and practice fundamental concepts of time series analysis using pandas in Python, including creating time series, resampling, rolling statistics, and visualizations.

### Create a Synthetic Time Series Dataset

import pandas as pd
import numpy as np

# Generate date range
date_rng = pd.date_range(start='2023-01-01', end='2023-12-31', freq='D')

# Generate random values between -5 and 5
data = np.random.uniform(-5, 5, size=len(date_rng))

# Create a pandas Series
ts = pd.Series(data, index=date_rng)
ts.name = "Random Values"

# Display first few rows
print(ts.head())


### Time-based Slicing

##### Data for January 2023
jan_data = ts['2023-01']
print("January 2023 Data:")
print(jan_data)

##### Data from March 15 to March 31, 2023
march_data = ts['2023-03-15':'2023-03-31']
print("March 15-31, 2023 Data:")
print(march_data)


### Resampling

##### Resample to monthly mean
monthly_mean = ts.resample('M').mean()
print("Monthly Mean:")
print(monthly_mean)

##### Resample to weekly sum
weekly_sum = ts.resample('W').sum()
print("Weekly Sum:")
print(weekly_sum)


### Shifting

##### Shift forward by 1 day
shifted_forward = ts.shift(1)
print("Shifted Forward (1 Day):")
print(shifted_forward.head())

##### Shift backward by 1 day
shifted_backward = ts.shift(-1)
print("Shifted Backward (1 Day):")
print(shifted_backward.head())

##### Visualization
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))
ts.plot(label='Original', alpha=0.7)
shifted_forward.plot(label='Shifted Forward (1 Day)', alpha=0.7)
shifted_backward.plot(label='Shifted Backward (1 Day)', alpha=0.7)
plt.legend()
plt.title('Original vs. Shifted Series')
plt.show()


![output_5_1](https://github.com/user-attachments/assets/d06970f3-f478-4080-96ac-a5e222b39b2d)


### Rolling Statistics

##### 7-day and 30-day rolling mean
rolling_7 = ts.rolling(window=7).mean()
rolling_30 = ts.rolling(window=30).mean()

##### Visualization
plt.figure(figsize=(10, 6))
ts.plot(label='Original', alpha=0.5)
rolling_7.plot(label='7-Day Rolling Mean', alpha=0.8)
rolling_30.plot(label='30-Day Rolling Mean', alpha=0.8)
plt.legend()
plt.title('Rolling Statistics')
plt.show()


![output_6_0](https://github.com/user-attachments/assets/958a4d18-88a6-46bc-a05b-bc9a10ac810f)


### Visualization

##### Plot the time series
plt.figure(figsize=(12, 6))
ts.plot()
plt.title('Time Series Visualization')
plt.xlabel('Date')
plt.ylabel('Random Values')
plt.grid(True)
plt.show()



![output_7_0](https://github.com/user-attachments/assets/2834bd73-4f94-423a-92b8-fdc5fa5db5b2)
