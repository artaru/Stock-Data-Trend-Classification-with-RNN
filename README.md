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
Data was collected using [polygon.io](https://polygon.io/), yielding 1-minute timespan **META** stock data, that includes Datetime, Open, High, Low, Close, Volume, as well as Volume weighted Average Price (VW)	and Number of Rransactions (N) for each minute. 
![image](https://github.com/artaru/Stock-Data-Classification-with-RNN/assets/79018762/17bd5a4e-c060-4777-9f9a-e1d147b3b51d)

Original data was processed by extracting dates, filtering out incomplete days, grouping the data by day, creating a list of DataFrames, each representing a complete day of data. As a result we were able to get 440 complete days from _2022-06-09 09:30:00_ to _2024-03-15 15:59:00_. 

##  Training and Testing Data
The first 400 days will be used for model training and validation sets while the last 40 days for trading performance analysis using the trained model. 
In ordet to generate training and testing dataset we will iterates over a subset of daily data frames, extracting price and volume information. A sliding window approach was used to generate features and labels (X and Y), where each feature consists of ratios of consecutive prices and volumes. Following each window, we cluster prices, fiting linear regressions, and detecting outliers until a threshold is reached or the day ends. When a coefficient of the following cluster is obtained, we assign a label (y) based on the slope of the linear fit, where a positive slope corresponds to 1 and a negative slope corresponds to 0.  At the end, we assemble the features and labels into numpy arrays for further processing.

Note on Trend Clustering Process: The code initializes an empty list l_cluster to store prices within a cluster, It starts iterating from the end of the sliding window, adding prices to the l_cluster until either an outlier is detected or the end of the day is reached. This process aims to capture a sequence of consecutive prices that might exhibit a trend, which could be either increasing or decreasing.
The threshold parameter is utilized to determine whether a data point is considered an outlier. Once a cluster is formed, a linear regression model is fitted to it. The residual values are calculated, if any residual value exceeds a certain threshold, it indicates a significant deviation from the linear trend, suggesting the presence of an outlier.
![image](https://github.com/artaru/Stock-Data-Classification-with-RNN/assets/79018762/9e4e918b-62f6-46d0-852f-3d7de5580f8a)





