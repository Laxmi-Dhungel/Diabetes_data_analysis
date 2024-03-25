# Diabetes_data_analysis_report-kaggle
This is a report analyzing diabetes data ontained from kaggle dataset (https://www.kaggle.com/datasets/zain280/diabeties-dataset/data). The data contains various attributes such as Number of pregnancies, Glucose, Blood pressure, skin thickness, Insulin, Body Mass Index (BMI), Diabetes pedigree Function, and age of patients with diabetes or at a risk of diabetes (ref: https://www.kaggle.com/datasets/zain280/diabeties-dataset/data). In this report, I performed data cleaning and validation and analysis of above factors in determining diabetes outcome.   

**Data cleaning and validation steps**

The data cleaning and validation steps is summarized in figure . 
Data cleaning is one of the most important steps in data analysis as real-world data is never in its purest form. There can be several missing values, misspellings, typos errors among several other types of error that can be present in data. As a first step of data analysis, I explored the data type of each column in the data. The data were either integer or float. The shape of the data showed that there are 769 rows and 9 columns.

<img width="292" alt="data_types_shape" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/7372c2ed-b677-43eb-80a4-ff309faf33b1">

Figure 1. Data columns and their data types. The data type were either integer or float. The data shape showed 769 rows and 9 columns. 


I further explored each numerical variable to see their distribution of values. The aummary statistics showed that minimum values for glucose, blood pressure, skin thickness, insulin and BMI were unusual (minimum 0). The values for these attributes cannot be 0, hence suggested some sort of error. I further looked at the value counts of each outcome. There were two unique values 0 and 1 with counts of 500 and 269 respectively. There were no duplicate and missing values.  I further counted the total number of rows with value 0 for columns glucose, blood pressure, skin thickness, insulin, and BMI. The total number of rows with values 0 were less than 5% for Glucose, Blood pressure and BMI whereas they were higher for Skin thickness and Insulin column. Hence, I removed rows with value 0 for Glucose, Blood pressure and BMI column. 

<img width="470" alt="descriptive data_all" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/05a469bf-70bd-4d2a-8468-74fce368ab6b">
Figure 2. Summary statistics of each column. The summary statistics showed unusual minimum value (0) for columns glucose, blood pressure, skin thickness, insulin and BMI.

<img width="267" alt="value_zer_percentage" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/e0dd45f1-5c51-4f4b-a0f2-95460d128637">
Figure 3. Total count of rows with values 0 for columns glucose, blood pressure, skin thickness, Insulin and BMI. The data percentages for value 0 was lesser than 5% for columns glucose, blood pressure and BMI whereas greater than 5% for insulin and skin thickness. 
