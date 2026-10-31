# Ex.No: 03   COMPUTE THE AUTO FUNCTION(ACF)
Date: 31-10-2026 

### AIM:
To Compute the AutoCorrelation Function (ACF) of the data for the first 35 lags to determine the model
type to fit the data.

### Dataset Name : AirPassenger
### ALGORITHM:
1. Import the necessary packages
2. Find the mean, variance and then implement normalization for the data.
3. Implement the correlation using necessary logic and obtain the results
4. Store the results in an array
5. Represent the result in graphical representation as given below.
### PROGRAM:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
df = pd.read_csv("AirPassengers.csv")
df = df.dropna(subset=["#Passengers"])
data = df["#Passengers"].to_numpy()
N = len(data)
lags = range(35)
mean_data = np.mean(data)
variance_data = np.var(data)
normalized_data = (data - mean_data) / np.sqrt(variance_data)
autocorr_values = []
for lag in lags:
    if lag == 0:
        autocorr_values.append(1)
    else:
        auto_cov = np.sum(
            normalized_data[:-lag] * normalized_data[lag:]
        ) / N
        autocorr_values.append(auto_cov)
plt.figure(figsize=(10,6))
plt.stem(lags, autocorr_values)
plt.title("Autocorrelation Function (ACF) of Air Passengers")
plt.xlabel("Lag")
plt.ylabel("Autocorrelation")
plt.grid(True)
plt.show()
```
### OUTPUT:
<img width="907" height="548" alt="image" src="https://github.com/user-attachments/assets/d06807e7-e455-4fd1-b726-bfbc8445f78c" />


### RESULT:

Thus we have successfully implemented the auto correlation function in python.
