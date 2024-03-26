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


I sorted the unique values for each of these columns to determine the second minimum values. The values looked okay for all the other columns except the Insulin column where the second minimum value was 1. There was only one row with an insulin value of 1 hence I removed that row. Since the percentage of data with value 0 for Skin thickness and Insulin columns were >20%, I did not want to impute them with mean or median value. Thus, I used machine learning to replace values 0 for these columns. 

I first divided data into 4 categories. 
1.	Data with no zero on both skinthickness and insulin column
2.	Data with zero value in both skinthickness and insulin column
3.	Data with value zero in only insulin column
4.	Data with value zero in only skin thickness column


I rechecked the divided data to confirm that they contain values as expected (zeros and non_zeros). I then used linear regression to predict and replace the values 0 with predicted values for insulin and skin thickness column. After replacing values 0 with predicted values for each divided dataset, I concatenated these divided data to generate a new updated data. There was no data with skin thickness value as zero and insulin as non-zero. The shape of updated data was same as data before division hence confirming that this way of dividing data and concatenating later did not impact data structure. 

<img width="431" alt="data division" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/6d14c786-41e6-4008-bda5-caac8c5e0b24">


<img width="605" alt="linreg_insulin_skinthickness" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/992e065c-367a-4e1f-8f77-0e3c9d83e665">


<img width="418" alt="concat_data-divided" src="https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/9ec0554f-b36c-4231-bfbf-60c3fbc40267">


![Data_cleaning_and_validation_steps](https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/9b4dfacc-5a4d-4c28-a9e4-029698fc25f0)


Figure 4. Summary of data cleaning and validation steps for diabetes data obtained from kaggle datasets. The data did not have any duplicate and missing values. However, summary statistics showed unsual values 0 for columns glucose, blood pressure, skin thickness, insulin and BMI. Theses values cannot be 0 and could be assigned 0 for missing values. The data percentages of values 0 were lesser than 5% for glucose, blood pressure and BMI columns. Hence, these rows with values 0 were removed for these columns. The data percentages with values 0 were higher than 5% for insulin and skin thickness columns hence these data were not removed. Since, the data percentages were even higher than 20%, the data were not imputed using mean or median. The insulin and skin thickness with values 0 were predicted based on other columns using linear regression. 




**Data Analysis**


**Distribution of data for each attribute**


I generated histograms to visualize the distribution of data for each attribute for each disease. The data were not normally distributed for each attribute when grouped based on outcome. Also, there were outliers present in the data. Hence, median was used for analysis of these attributes. 




![data_dist_part1](https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/d3b824af-a05b-468a-ada3-ff757230f61c)

Figure 5. Histogram showing data distribution for different attributes for each disease outcome. A) Age, B) Number of pregnancies, C) BMI, D) Diabetes Pedigree Function. Outcome=0 (Non-diabetic), Outcome=1 (Diabetic). For each attribute, the data was not normally distributed and there were outliers present.


![data_dist_part2](https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/12adf675-fe5c-4f84-b9ef-cbac4ef669e4)

Figure 6. Histogram showing data distribution for different attributes for each disease outcome. A) Glucose, B) Insulin, C) Blood Pressure, D) Skin Thickness. Outcome=0 (Non-diabetic), Outcome=1 (Diabetic). The data were not normally distributed and had outliers.


**Impact of age on Diabetes outcome**

The age was divided into different categories with 5-year intervals. The diabetic percentages for each age category were determined. The age group 51-55 had the highest percentages of diabetic patients. The age group >70 had the lowest diabetic percentage (0%). However, this could be due to low data for these group patients (there was only 1 data). The age group 21-25 had the second lowest percentages of diabetic patients. The data showed a decline in percentages of diabetic patients at older ages. However, the data was skewed and had lower frequency of population at the older ages which may be one of the reason contributing to the observed lower percentages of diabetic patients at these ages.  


![Age_diabetic_percentages](https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/d00096bc-034b-4d9c-bda1-7c5d2faaee63)

Figure 7. The line graph showing percentages of diabetic patients for each age cattegory. The age was divided into different categories with 5-year intervals. The age-group 51-55 had highest percentages of diabetic patients. There was only 1 data for age-group >70. When this group (>70) was considered then the age group 21-25 had the lowest percentages of diabetes patients.



**Impact of pregnancy on diabetes outcome**

To study the effect of number of pregnancies on diabetes outcome, the median number of pregnancies for each diabetic outcome was determined. The median number of pregnancies for diabetic patients (4) was significantly higher than the non-diabetic patients (2). Further, the median number of pregnancies for diabetic and non-diabetic patients for different age-groups was determined. The age groups 21-25y, 26-30 y, 36-40 y and 46-50 y had higher median number of pregnancies in diabetic patients whereas age-groups 31-35 y, 56-60 y, 61-65 y and 66-70 y had lower median number of pregnancies in diabetic patients. However, the median number of pregnancies was not significantly different for any age-group (Mann-whitneyU test, P<0.05).

Further, the data was divided into two groups (<4 pregnancies and >=4 pregnancies) based on the number of pregnancies. The number 4 was chosen because it is the median number of pregnancies in the diabetic patients. The results showed higher percentages of diabetic patients with number of pregnancies greater or equal to 4 (44.8%) compared to number of pregnancies <4 (26.13%). The chi square test showed significant association between number of pregnancies (<4 pregnancies and >=4 pregnancies) and diabetes outcome (P<0.05). The odds ratio (2.26) and relative risk (1.4) for diabetes were also higher in patients with greater or equal to 4 pregnancies. 


![Pregnancies_boxplot](https://github.com/Laxmi-Dhungel/Diabetes_data_analysis-kaggle/assets/154451345/984224df-521e-487f-bbec-dc3f09316305)

Figure 8. Boxplot showing median number of pregnancies for each diabetes outcome. The media number of pregnancy was significantly higher for diabetic patients compared to non-diabetic patients (Mann-whitney U test, p<0.05). The Diabetes outcome 0 represent non-diabetic patients whereas Diabetes Outcome 1 represent diabetic patients. 

