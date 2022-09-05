# Brazil(Southeast) Weather Dataset 
Calvin Yu
## Abstract 
The goal of this project is to understand how the temperature changes though out the time, and to make educated prediction on the temperature for the future. I downloaded the dataset from kaggle.com. The dataset was originally written in Spanish, so I had to change the column names to English for comprehension. It is huge with fifty millions data points along with twenty five columns from 2000 to 2021. I have done data manipulation to fill up the missing values, and drop some columns to avoid multicollinarity.
Also, I did a quick data visualization with the target variable. Then, I applied different machine learning algorithms to train the dataset to see which one can predict the future the best.
## Design
The government of Brazil wants to keep track of the weather for its territory, however, some stations failed to record. So the government would like someone to help them fix the dataset, and to make educated guess on the future temperature. So my job is to fix the dataset and use machine learning models to predict the future temperature.
## Data
### Brazil Southeast Dataset
- From 2000 to 2021
- 15345216 rows with 27 original feature columns and 1 target variable 
- feature highlights:  date, hour, total precipitation (mm),radiation (kj/m2), air temperature - dry bulb (°c),dew point temperature (°c), air relative humidity (%),
wind direction (° (gr)), wind rajada maxima (m/s),
## Algorithms 
1. Use Python to read the dataset, translate the columns to english for readibility
2. Check for missing values , figure out -9999 is the missing value, replace all -9999 to Nan
3. Grouping station, month, and hour to find the average value for all the columns that contain missing values and use the average values to fill with all missing values 
4. Fill up the rest of the missing values using front-fill 
5. Use heatmap to find columns with multicolinarity and drop them accordingly 
6. Since the dataset is too large, I only choose Casa Branca to do the forcast
7. Dropping state,station,latitude,longitude,and height becase I am only examing the same station
8. The columns that I am using are 	month,hour,total precipitation (mm)	radiation (kj/m2),air temperature - dry bulb (°c),dew point temperature (°c),air relative humidity (%),wind direction (° (gr)),wind rajada maxima (m/s),wind speed (m/s) with air temperature- dry bulb(°c) as the target variable
9. Split the dataset into test,train,validation, and use kfold to shuffle up the validation set to get a more accurate result
10. Apply the training set with Linear Regression, Lasso, Ridge 
11. For Lasso and Ridge, use CV to find the best alpha to fit into the model and standardize the training set to get a higher quality results
12. Use r2 score as the metric to measure to predictability for each model 
<img width="273" alt="Screen Shot 2022-09-04 at 6 19 10 PM" src="https://user-images.githubusercontent.com/63031028/188342504-c1bc6af6-9ce1-4696-a39a-7c58b09d14a9.png">
13. Try using the dataset on Time Series model 
14. Use auto arima to get the best time series model for use 
15. Use seasonal decompose to evaluate the trend of the data
16. Fit the dataset to SARIMAX along with the exogenous columns as the columns other than the target variable
![image](https://user-images.githubusercontent.com/63031028/188343416-07152453-a73d-4c3b-af44-c8032433ac91.png)
17. Try using the time series model on the ALFREDO CHAVES station 
![image](https://user-images.githubusercontent.com/63031028/188343550-88250294-952a-4011-b37d-61896cb3ff45.png)
18. Compare the results of all the model that I used and choose either Ridge or time-series to do the forecast

<img width="640" alt="Screen Shot 2022-09-04 at 6 37 49 PM" src="https://user-images.githubusercontent.com/63031028/188343751-eca62ce8-77ea-431a-9938-2da8373016fc.png">

## Tools
- Numpy,Pandas - Data cleaning 
- Matplotlib, Seaborn - Exploratory data analysis 

- Scikit learn - Machine Learning Algorithms,
- Pmdarima - Getting the best time-series model 
- Tableau - Data visualization 
## Communication 
- The Ridge regression gives us the best result after feeding it with the features other than the actual time stamp. But it still performs really well in predicting the future
- The Time-series model takes the time variable and the other columns as exogenous features to forecast the results and it does pretty well with 94% of accuracy 
- We can use these two models intercharables depending on the situation 

## Future Steps
- I have only done machine learning algoritms on one station, if i have more time , I will try to do more 
- If I have a better computer, I will take the dataset as whole and take latitude and longitude into considerion on  predicting the  temperature 
## Takeaways 
- Get more familiar with Linear regression model, Ridge , Lasso ,and the time-series model 
- Develop a good way to deal with missing values

