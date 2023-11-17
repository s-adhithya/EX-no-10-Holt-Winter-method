# EX-no-10-Holt-Winter-method
## AIM:
To implement the holt winters method using python program

## Procedure:
1.Import necessary libraries , Matplotlib for plotting, and Pandas for data handling.

2.Create an Exponential Smoothing model (Holt-Winters) using statsmodels. Configure the model with trend and seasonal components.

3.Creating a time series plot with a specified time range that includes the forecast.

4.Generate a long-term forecast by forecasting future values for the entire time series.

## Program
```
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.api import ExponentialSmoothing, SimpleExpSmoothing, Holt
airline  = pd.read_csv('/content/AirPassengers.csv',index_col='Month',parse_dates=True)
airline.index.freq = 'MS'
airline.index
airline.tail()
len(airline)
train_airline = airline[:108]
test_airline = airline[108:]
len(test_airline)
fitted_model = ExponentialSmoothing(train_airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()
test_predictions = fitted_model.forecast(36).rename('HW Test Forecast')
test_predictions[:10]
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
plt.title('Train and Test Data');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION')
plt.title('Train, Test and Predicted Test using Holt Winters');
train_airline['#Passengers'].plot(legend=True,label='TRAIN')
test_airline['#Passengers'].plot(legend=True,label='TEST',figsize=(12,8))
test_predictions.plot(legend=True,label='PREDICTION',xlim=['1958-01-01','1961-01-01']);
from sklearn.metrics import mean_absolute_error,mean_squared_error
print(f'Mean Absolute Error = {mean_absolute_error(test_airline,test_predictions)}')
print(f'Mean Squared Error = {mean_squared_error(test_airline,test_predictions)}')
test_airline.describe()
final_model = ExponentialSmoothing(airline['#Passengers'],trend='mul',seasonal='mul',seasonal_periods=12).fit()

forecast_predictions = final_model.forecast(steps=36)
airline['#Passengers'].plot(figsize=(12,8),legend=True,label='Current Airline Passengers')
forecast_predictions.plot(legend=True,label='Forecasted Airline Passengers')
plt.title('Airline Passenger Forecast')
```
## Output:
### airline.index
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/c600b238-5524-4975-95fd-5b4f7c88bd6e)


### airline.tail()
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/8b912917-d537-419b-b282-d32b31cbf6ec)


### len(airline)
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/8e420878-9ad0-46b7-bb21-9d8456093d60)


### len(test_airline)
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/32d83512-a552-4e08-bc9c-6141ea833b05)


### test_predictions[:10]
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/11dc50b0-02b1-4763-8fee-b6fbe004a339)


### Train and Test Data Graph
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/b2d86955-e85f-4437-b292-e1f33d0fda01)


### Train, Test and Predicted Test using Holt Winters graph
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/3e7cbeea-52f4-4da3-a79e-9098cf81c566)


### Prediction Graph
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/518d4ca1-1209-4740-b561-0aaa93b35ba9)


### Mean Absolute Error
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/49b87b15-841a-4f46-a379-5325b0cb79f9)


### Mean Squared Error
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/ad78e63d-4b55-40a2-aea9-c67e2966f0a8)


### test_airline.describe()
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/2902f829-32d2-4d9d-aee6-1630a88cf7a4)


### Airline Passenger Forecast Graph
![image](https://github.com/s-adhithya/EX-no-10-Holt-Winter-method/assets/113497423/855461f5-0832-47b5-8364-e6fdddd39128)


## Result:
Thus the program to implement holt winters method is written and verified using python programming.
