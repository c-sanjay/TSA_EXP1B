# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA
## Date: 02/05/2025
### NAME : SANJAY C
### REG NO : 212223240150

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on international airline passenger data
### REQUIREMENTS:
```
1.DATASET : APPLE STOCK PRICE
2.TECHNOLOGY USED : GOOGLE COLLAB
```
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
```PY
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


data = pd.read_csv('apple.csv', parse_dates=['Date'])
data.set_index('Date', inplace=True)

data['volume_diff'] = data['Volume'].diff()
data['volume_log'] = data['Volume'].apply(lambda x: np.log(x) if x > 0 else np.nan)
data['volume_log_diff'] = data['volume_log'].diff()

data['volume_sea_diff'] = seasonal_decompose(data['Volume'], model='additive', period=12).residcleaned_volume_log_diff = data['volume_log_diff'].dropna()
if len(cleaned_volume_log_diff) >= 2 * 12:
    data['volume_log_seasonal_diff'] = seasonal_decompose(
        cleaned_volume_log_diff, model='additive', period=12
    ).resid
else:
    print("Warning: Not enough data for seasonal decomposition after cleaning 'volume_log_diff'.")
    data['volume_log_seasonal_diff'] = pd.Series(index=data.index, dtype=float) 


plt.figure(figsize=(16, 16))

plt.subplot(6, 1, 2)
plt.plot(data['volume_diff'], label='Regular Difference')
plt.title('Regular Differencing')
plt.xlabel('Year')
plt.ylabel('Differenced Volume')
plt.legend()

plt.subplot(6, 1, 3)
plt.plot(data['volume_sea_diff'], label='Seasonal Adjustment')
plt.title('Seasonal Adjustment')
plt.xlabel('Year')
plt.ylabel('Seasonally adjusted Volume')
plt.legend()

plt.subplot(6, 1, 4)
plt.plot(data['volume_log'], label='Log Transformation')
plt.title('Log Transformation')
plt.xlabel('Year')
plt.ylabel('Log(Volume)')
plt.legend()

plt.tight_layout()
plt.show()
```

### OUTPUT:


#### REGULAR DIFFERENCING:
<img width="1664" height="306" alt="image" src="https://github.com/user-attachments/assets/5dec3d89-e674-48a0-bcf9-7197224d17bd" />

#### SEASONAL ADJUSTMENT:
<img width="1665" height="289" alt="image" src="https://github.com/user-attachments/assets/095fd266-7cf3-4719-b788-00371d5978f5" />


#### LOG TRANSFORMATION:
<img width="1660" height="291" alt="image" src="https://github.com/user-attachments/assets/4f340358-ac05-4735-9f37-a59367b61582" />



### RESULT:
Thus we have created the python code for the conversion of non stationary to stationary data on international airline passenger
data.
