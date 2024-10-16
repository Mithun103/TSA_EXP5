# Ex.No: 05  IMPLEMENTATION OF TIME SERIES ANALYSIS AND DECOMPOSITION
### Date: 


### AIM:
To Illustrates how to perform time series analysis and decomposition on the monthly average temperature of a city/country and for airline passengers.

### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the decomposition process for the required data.
4. Plot the data according to need, either seasonal_decomposition or trend plot.
5. Display the overall results.

### PROGRAM:
```
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose


df = pd.read_csv('ECOMM DATA.csv') 

print(df.head())

df['Order Date'] = pd.to_datetime(df['Order Date'])
df.set_index('Order Date', inplace=True)

price_data = df['Profit']

new_index = pd.date_range(start=price_data.index.min(), periods=len(price_data), freq='B')[:len(price_data)]
price_data.index = new_index

decomposition = seasonal_decompose(price_data, model='additive', period=365)

trend = decomposition.trend
seasonal = decomposition.seasonal
residuals = decomposition.resid

plt.figure(figsize=(12, 6))
plt.plot(price_data, label='Profit')
plt.title('Profit')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(seasonal, label='Seasonal Component', color='orange')
plt.title('Seasonal Component')
plt.legend()
plt.show()

plt.figure(figsize=(12, 6))
plt.plot(trend, label='Trend Component', color='green')
plt.title('Trend Component')
plt.legend()
plt.show()

plt.plot(residuals, label='Residuals', color='red')
plt.legend(loc='best')
plt.tight_layout()
plt.show()
```


### OUTPUT:
FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/8cd02c1c-e247-4dc1-a86e-2e72e265a891)



PLOTTING THE DATA:

SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/66869198-f415-4cb4-bfc9-f1e0d849929c)

![image](https://github.com/user-attachments/assets/40fd7a48-3716-47fd-b665-526947f27252)



TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/bee9fca7-25f9-4228-a176-3326a7d4dbfe)

OVERAL REPRESENTATION:

![image](https://github.com/user-attachments/assets/e46892a1-8eec-4a21-a38a-26007335d286)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
