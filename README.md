# DEVELOPED BY : SHALINI K
# REGISTER NUMBER : 212222240095
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
```py
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose

# Load the Bitcoin dataset
file_path = 'coin_Bitcoin.csv'  # Update with the correct file path
data = pd.read_csv(file_path)

# Convert the 'Date' column to datetime format and set it as the index
data['Date'] = pd.to_datetime(data['Date'], format='%Y-%m-%d %H:%M:%S')
data.set_index('Date', inplace=True)

print("FIRST FIVE ROWS:")
print(data.head())

# Extract the 'Close' column (Bitcoin closing price)
bitcoin_close = data['Close']

# Plot the Bitcoin close price data
plt.figure(figsize=(12, 6))
plt.plot(bitcoin_close, label='Bitcoin Close Price')
plt.title('Bitcoin Close Price Over Time')
plt.legend()
plt.show()

# Perform time series decomposition
# Assuming daily periodicity (Bitcoin market operates continuously)
period = 365  # Assuming yearly seasonality for the purpose of decomposition
result = seasonal_decompose(bitcoin_close, model='multiplicative', period=period)

# Plot the decomposition components
plt.figure(figsize=(12, 8))

# Seasonal Plot Representation
print("\nSEASONAL PLOT REPRESENTATION:")
plt.figure(figsize=(12, 4))
plt.plot(result.seasonal, label='Seasonal', color='green')
plt.title('Seasonal Component of Bitcoin Close Price')
plt.legend()
plt.show()

# Trend Plot Representation
print("\nTREND PLOT REPRESENTATION:")
plt.figure(figsize=(12, 4))
plt.plot(result.trend, label='Trend', color='yellow')
plt.title('Trend Component of Bitcoin Close Price')
plt.legend()
plt.show()

# Original time series
plt.figure(figsize=(12, 4))
plt.plot(bitcoin_close, label='Original')
plt.title('Original Bitcoin Close Price Time Series')
plt.legend()
plt.show()
```
### OUTPUT:
# FIRST FIVE ROWS:
![image](https://github.com/user-attachments/assets/aba8b2c4-f4ee-4359-85a7-09546f11583d)

# PLOTTING THE DATA:
![image](https://github.com/user-attachments/assets/1ff3c73d-941d-44b1-96a1-e747319db536)


# SEASONAL PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/50188ebd-4f04-4eab-aa0f-fac90cc79aac)

# TREND PLOT REPRESENTATION :
![image](https://github.com/user-attachments/assets/19a94cb7-4674-4912-9c27-ea2784475357)


# OVERAL REPRESENTATION:
![image](https://github.com/user-attachments/assets/b5967bac-cf95-4f26-96ee-fca3b43249c7)


### RESULT:
Thus we have created the python code for the time series analysis and decomposition.
