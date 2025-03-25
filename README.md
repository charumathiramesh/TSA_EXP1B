# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```c
 import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```
```c
data = pd.read_csv('/content/IOT-temp.xls')
```
```c
print(data.head())
```
```c
plt.figure(figsize=(10, 5))
# Assuming 'noted_date' is the actual column name in your data
plt.plot(data['noted_date'], data['temp'], label='Original Data')
plt.xlabel('noted_date')
plt.ylabel('temp')
plt.title('Temperature Data - Original')
plt.legend()
plt.show()
```
```c
data['Diff'] = data['temp'].diff()
data.dropna(inplace=True)
plt.figure(figsize=(10, 5))
plt.plot(data['noted_date'], data['Diff'], label='Differenced Data')
plt.xlabel('noted_date')
plt.ylabel('temp Difference')
plt.title('Temperature Data - Regular Differencing')
plt.legend()
plt.show()
```
```c
!pip install statsmodels
import statsmodels.api as sm
from statsmodels.tsa.seasonal import seasonal_decompose # Import seasonal_decompose

period = 12  # Adjust based on data frequency (e.g., monthly data -> 12)
decomposition = seasonal_decompose(data['temp'], period=period, model='additive', extrapolate_trend='freq')
data['Seasonally_Adjusted'] = data['temp'] - decomposition.seasonal

plt.figure(figsize=(10, 5))
plt.plot(data['noted_date'], data['Seasonally_Adjusted'], label='Seasonally Adjusted Data')
plt.xlabel('noted_date')
plt.ylabel('Seasonally Adjusted Temp')
plt.title('Temperature Data - Seasonal Adjustment')
plt.legend()
plt.show()

```
```c
data['Log'] = np.log(data['temp'])
data.dropna(inplace=True)
plt.figure(figsize=(10, 5))
plt.plot(data['noted_date'], data['Log'], label='Log Transformed Data')
plt.xlabel('noted_date')
plt.ylabel('Log(temp)')
plt.title('Temperature Data - Log Transformation')
plt.legend()
plt.show()
```

### OUTPUT:

ORIGINAL DIFFERENCING:

![download](https://github.com/user-attachments/assets/8b22b986-2819-46eb-b5bb-0ea46ae60ddd)


REGULAR DIFFERENCING:

![download](https://github.com/user-attachments/assets/48412b37-4a89-4ae5-b2e6-1cfa1e2aff55)



SEASONAL ADJUSTMENT:

![download](https://github.com/user-attachments/assets/13e938d1-2de9-4c1d-892a-858585a0fc9f)



LOG TRANSFORMATION:

![download](https://github.com/user-attachments/assets/338128d3-c0cb-472f-aa9a-11cebe4ff10c)


### RESULT:

Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
