# MSCS 634 Advanced Data Mining and Big Data
# [Lab 1: Data Visualization, Data Preprocessing, and Statistical Analysis]

**Name:** Nischal JOshi
**Lab Title:** Lab 1 - Data Visualization, Data Preprocessing, and Statistical Analysis Using Python in Jupyter Notebook

## Lab Overview
The lab performs data analysis on a dataset extracted from the kaggle for walmart sales. The goal of this lab is to load the dataset, visualize it and preprocess to perform  statistical analysis to extract insights.
The dataset being used has 8 columns [ Store, Date, Weekly_Sales, Holiday_Flag, Temperature, Fuel_Price, CPI, Unemployment]

## Key Steps and Techniques

### Loading Data: 
  <img width="807" alt="head" src="https://github.com/user-attachments/assets/2cb5387b-a219-465a-9741-692df3fd4993" />

   Loaded dataset using `pandas.read_csv()` and displayed the first few rows using `.head()`

### Data Visualization
  <img width="807" alt="data visualization" src="https://github.com/user-attachments/assets/1aaba84a-5cce-44ec-bd90-7ba971df4262" />

- **Scatter Plot of Weekly Sales vs Fuel Price.**:
    It Represents the relation between weekly sales in x-axis and fuel prices in y-axis.
    As per the scattered distribution of the points, there isn't any specific linear relationship between the two columns.
    The sales are spread across a wide range of fuel prices (~$2.50 to ~$4.50) instead of forming a specifc upward or downward trend 
    
- **Bar Plot**: Average Weekly Sales per Store.**:
    The x-axis represents the store number from 1 to 45 and the y-axis represnets the average weekly sales in $.
    Store no 4, 14, 20 and 27 have the highest weekly average sale (above 2 million).
    Stire 33 to 45 have lower average weekly sales indicating under performance of the store.
    The significant variation could be caused by various factors like store size, inventory, location and management strategies.
    

### Data Preprocessing
- **Missing Values**:

  <img width="807" alt="missing_values" src="https://github.com/user-attachments/assets/df29ffd0-61bf-4688-9296-5b281e9395de" />
  
    The missing value is detected using .isnull() method. 
    There are total of 6 data missing in the Fuel_Price Column. 
    The missing value of items are replaced with the mean value. 
    
- **Outliers**: Detected and removed using IQR technique
  <img width="755" alt="outliers-" src="https://github.com/user-attachments/assets/e90ccdf2-1d04-42bc-a10d-1a5b222b1e00" />

    To improve the quality, the outliers from the Weekly_Sales column are removed using InterQuartile Range (IQR) method.
    The Q1 (25th Percentile) is 553,350.10 and Q3 the (75th Percentile) value is 1420158.66
    IQR (Q3-Q1) = 866,808.55
    The lower bound is calculated as (Q1 – 1.5 × IQR) = –746,682.73
    The Upper Bound is calcualted as (Q3 + 1.5 × IQR) = 2,720,371.49
    Any value falling outside these bounds are flagged as outliers. 
    Total outliers detected: 34
    Some sample outliers include
    Store 2: Weekly Sales = 3,436,007.68
    Store 24: Weekly Sales = 3,224,369.80
    Store 14: Weekly Sales = 2,784,969.45
    
    Before removing  outlier: 6435 rows 
    After removing  outliers: 6401 row
    
    The removal ensures a more accurate analysis.
    
- **Data Reduction**:
  
  <img width="564" alt="data_reduction" src="https://github.com/user-attachments/assets/f90e0210-a194-48da-ab3f-87805127db2a" />

    For data reduction 50 percent of the data were used as sampled.
    Also, dimension elimination was performed by dropping a less relevant column i.e CPI column.

- **Scaling/Discretization**:
  
  <img width="793" alt="data-before-scaling" src="https://github.com/user-attachments/assets/41b75ea8-6d4a-4ffc-a1b5-f58429d3b77a" />
  
    Applied Min-Max Scaling and Z-score scaling.
    The Min-Max Scaling is calculated as (X-Xmin)/(Xmax-Xmin) and the generated value stays between 0 to 1.
    The Z-score standardization is calculated as (X−μ)/σ
​	
  <img width="793" alt="after_scaling_z_score_standardization" src="https://github.com/user-attachments/assets/2631e17e-2586-448d-ad44-3022b3ff5edd" />

    The Discretization was conducted in the Temperature column and was categorized as Low, High and Medium.
  
  <img width="793" alt="discretization_temperature" src="https://github.com/user-attachments/assets/29bd03a0-9927-459f-af86-d2c4820cacc7" />

### Statistical Analysis

  <img width="793" alt="info_describe" src="https://github.com/user-attachments/assets/5ac0df69-3739-468e-a38b-b832631e3af1" />
  
  Computed `.info()` and `.describe()` for dataset overview.
  
  <img width="793" alt="central_tendency_measure" src="https://github.com/user-attachments/assets/eaae810d-d1c6-4e77-a829-c31b3f2785b4" />
  
  Calculated central tendency measures: mean, median, mode.
  
  <img width="603" alt="dispersion" src="https://github.com/user-attachments/assets/012a4d9b-d1ca-42f8-9771-663e57100e66" />
  
  Computed dispersion metrics: range, IQR, variance, standard deviation.

  Generated a correlation matrix to identify relationships between numerical features.
 
  <img width="603" alt="correlation_matrix" src="https://github.com/user-attachments/assets/f068dee3-c164-468a-bbb2-06be7cd0ece1" />

  The correlation matrix value ranges from -1 to 1. 
  +1: Indicates perfect positive correlation.
   0: Indicates no linear correlation.
  -1: Indicates perfect negative correlation (as one increases, the other decreases).

## Key Insights
 - Tha analysis provides key insights into Walmart weekly sales data from 2010 to 2012. 

**Data Overview**:
- The dataset being used has 8 columns [ Store, Date, Weekly_Sales, Holiday_Flag, Temperature, Fuel_Price, CPI, Unemployment]
- The Fuel_Price has 6 missing items. 
- The Date column was successfully converted to datetime objects.

**Sale Performance and Trends**:
- The weekly sales are variable as per the store and time with a mean weekly sales of approximately $1 million. 
- The weekly sales showed a downward trend moving from 201o to 2012.

**Holiday Influence**:
- There is a clear seasonal patterns in the data set.
- Peaks occur during the November and Decemeber, which aligns with the holiday seasons.
- Weeks with Holiday_Flag have higher weekly sales in comparision to non-holiday weeks. 


**Impact of Environmental Factors** 
- There are weak correlation between Weekly_Sales and other economic and environmental indicators like CPI, Unemployement, Temperature and Fuel_Price.

**Data Distribution and Outliers**
- The Weekly_Sales how a right skewed distribution
- It highlights that majority of the weeks have lower sales value and only few instances of high sales.
- There are outliers present in all the columns.

## Key Challenges Faced
**Selecting Right Dataset**
- It was quiet challenging to find an appropiate dataset having correct size, numerical and categorical data and messy values to experiment with. 
- The weekly sales data of walmart was extracted from Kaggle and further modified to perform the analyis.

**Data Visualization**
- Choosing the right visual representation technique for effective interpretation of the data and trends required careful observation and understanding of data
- Making the visualization charts clear, readable and asthetically pleasing was time consuming and challenging.

**Data Reduction Handling and Dealing with Missing Values**
- Determing whether to impute or drop the missing values without affecting the integrity of the dataset was complicated. 

**Data Reduction** 
- Determing which column to remove or mannerism of data subsampling to use was a challenege as failing to do so may compromise the data integrity of the data.

