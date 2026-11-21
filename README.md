# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 20.11.2026
### Reg.No.: 212224240163
### Name: Subhash V

### AIM:
To illustrate how to perform time series analysis and decomposition on the monthly average temperature of India (10 major cities) using the Indian Climate Dataset for 2024–2025.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### DATASET:
Indian_Climate_Dataset_2024_2025.csv
### PROGRAM:

```py
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Step 1: Load the dataset, convert 'Date' to datetime
data = pd.read_csv('/content/Indian_Climate_Dataset_2024_2025.csv', parse_dates=['Date'])

# Step 2: Average the temperature of all 10 cities for each date,
# then take the monthly average (24 months = 2 full yearly cycles)
daily = data.groupby('Date')['Temperature_Avg (°C)'].mean()
monthly = daily.resample('MS').mean()

print(monthly.head())

# Step 3: Seasonal decomposition (12 months = 1 year)
decomposition = seasonal_decompose(monthly, model='additive', period=12)

# Step 4: Plot the decomposition
plt.figure(figsize=(10, 12))

plt.subplot(411)
plt.plot(monthly, label='Monthly Avg Temperature')
plt.legend(loc='upper left')
plt.title('Monthly Average Temperature (All Cities)')

plt.subplot(412)
plt.plot(decomposition.trend, label='Trend', color='orange')
plt.legend(loc='upper left')
plt.title('Trend Plot')

plt.subplot(413)
plt.plot(decomposition.seasonal, label='Seasonal', color='green')
plt.legend(loc='upper left')
plt.title('Seasonality Plot')

plt.subplot(414)
plt.plot(decomposition.resid, label='Residual', color='red')
plt.legend(loc='upper left')
plt.title('Residual Plot')

plt.tight_layout()
plt.show()
```


### OUTPUT:
FIRST FIVE ROWS:

<img width="855" height="237" alt="image" src="https://github.com/user-attachments/assets/5998fc28-261f-4a2a-bf2c-1253a5cdb23a" />



MONTHLY AVERAGE TEMPERATURE :

<img width="855" height="262" alt="image" src="https://github.com/user-attachments/assets/449a0cbf-c9b0-4f41-804b-3a00955f06ff" />

TREND PLOT REPRESENTATION :

<img width="845" height="252" alt="image" src="https://github.com/user-attachments/assets/63d151e5-ce55-465e-85cc-d405cea21e30" />


SEASONAL PLOT REPRESENTATION :

<img width="840" height="260" alt="image" src="https://github.com/user-attachments/assets/0b125496-4b66-4a9d-8460-cdc5e9c148bb" />

RESIDUAL PLOT :

<img width="865" height="247" alt="image" src="https://github.com/user-attachments/assets/8c3dc234-59b3-4039-a2be-194484760e4e" />




### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
