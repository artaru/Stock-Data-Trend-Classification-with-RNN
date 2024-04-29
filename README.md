# Stock Data Trend Classification with RNN

![](https://github.com/artaru/Stock-Data-Classification-with-RNN/blob/main/CreateCircle-ezgif.com-video-to-gif-converter.gif)

## Project Objective
The objective of this project is to leverage a Recurrent Neural Network for the detection of positive trends within intraday stock data. The model's input is characterized by a 20-minute range, while the subsequent trend is identified through a simple linear regression. 

### Methods Used
* Machine Learning
* Data Visualization
* Predictive Modeling
  
### Libraries  Used
* Numpy
* PyTorch
* Scikit-learn
* Matplotlib

## Original Data and Data Processing
Data was collected using [polygon.io](https://polygon.io/), yielding 1-minute timespan **META** stock data, that includes Datetime, Open, High, Low, Close, Volume, as well as Volume weighted Average Price(VW)	and number of transactions N for each minute. 
![image](https://github.com/artaru/Stock-Data-Classification-with-RNN/assets/79018762/17bd5a4e-c060-4777-9f9a-e1d147b3b51d)

Original data was processed by extracting dates, filtering out incomplete days, grouping the data by day, creating a list of DataFrames, each representing a complete day of data. As a result we were able to get 440 complete days from _2022-06-09 09:30:00_ to _2024-03-15 15:59:00_.


