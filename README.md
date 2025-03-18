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
import seaborn as sns
import holoviews as hv
hv.extension('bokeh')
```
```c
data=pd.read_csv('IOT-temp.csv')
```
```c
hv.Distribution(data['temp']).opts(
    title="Regular Distribution",
    color="blue",
    xlabel="Temperature",
    ylabel="Density",
    width=700,
    height=300,
    tools=['hover'],
    show_grid=True
)
```
```c
season_cnt = np.round(
    data['temp'].value_counts(normalize=True) * 100
)


hv.Bars(season_cnt).opts(
    title="Season Count",
    color="purple",
    xlabel="Season",
    ylabel="Percentage",
    yformatter='%d%%',
    width=700,
    height=300,
    tools=['hover'],
    show_grid=True
)
```
```c

data['log_temp'] = np.log(data['temp'].replace(0, np.nan))  
print(data[['temp', 'log_temp']].head())
plt.figure(figsize=(10, 6))
sns.histplot(data['log_temp'], kde=True)
plt.title('Log-Transformed Temperature Distribution')
plt.xlabel('Log Temperature')
plt.ylabel('Frequency')
plt.show()
```


### OUTPUT:


REGULAR DIFFERENCING:

![image](https://github.com/user-attachments/assets/f3346c45-d2b5-4c97-8b0e-baeb44f5c665)


SEASONAL ADJUSTMENT:

![image](https://github.com/user-attachments/assets/936c0071-3a4b-4900-b166-01c52464cd89)


LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/3f188ca5-583d-4e69-9396-dc6794cff0c3)


![image](https://github.com/user-attachments/assets/a8d418f3-6cf4-4bf8-a322-dd7fed12e662)


### RESULT:
we created code for nonstationary conversion to stationary conversion 


Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
