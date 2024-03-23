# Heart Disease Exploratory Data Analysis

### Project Overview
This project utilises EDA tools to explore the leading indicators of heart disease in the United States using survey data that was conducted by BRFSS. The insights gathered can help inform public health strategies, clinical interventions and personalized approaches to prevent, diagnose and prevent heart disease. Furthermore, the findings of indicators can be used in feature selection to gain a more comprehensive analysis using advanced methods such as regressions or machine learning models. 

![image](https://github.com/Tascha98/Heart-Disease-Exploratory-Data-Analysis/assets/135465320/3ca1eae6-a3ef-433b-91da-59723b7d5470)

### Data Sources
The primary dataset used for this analysis is the 2015 survey data sourced from the Behavioural Risk Factor Surveillance System (BRFSS). The BRFSS is the US’s premier system of telephone surveys on
gathering state-level data about health- related risk behaviors, chronic health conditions and utilization of preventive services among US residents.

### Tools
-Python

### Data Cleaning/ Preparation
The dataset contained 330 variables on 441456 respondents. The followig tasks were performed on dataset:
1. Variable Selection: Selected 14 relevant variables based on research papers (literature reviews, etc.)
2. Missing Value Handling
   
   -Identified missing values using non-null counts.
   
   -Dropped rows with missing data due to limitations of imputation methods in healthcare.
3. Data Formatting:
   
   -Cleaned survey data for clarity based on codebook definitions ([https://www.cdc.gov/brfss/annual_data/2015/pdf/codebook15_llcp.pdf.]).
   
   -Recoded categorical variables (e.g., _VEGLT1: 2 -> 0, 9 -> dropped).

### Exploratory Data Analysis
EDA was aimed to answer key questions such as :
1. What was the relationship between the variables and the target variable?
2. What was the distribution of the variables?
3. What were the feature variables that could be further used for complex models such as regression and machine learning models?

### Data Analysis

```python

# Compute the correlation matrix
correlation_matrix = ndf.corr()

# Create the correlation heatmap
plt.figure(figsize=(10, 8))  # Adjust the figure size if needed
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm', vmin=-1, vmax=1)
plt.title('Correlation Heatmap')
plt.show()

# Create two data subsets: one for heart disease present and one for heart disease absent
heart_disease_present = ndf[ndf['HeartDisease'] == 1]
heart_disease_absent = ndf[ndf['HeartDisease'] == 0]

# Combine the two subsets into a single DataFrame for plotting
data = pd.concat([heart_disease_present['BMI'], heart_disease_absent['BMI']], axis=1)
data.columns = ['Heart Disease', 'No Heart Disease']

# Plot the box plot
sns.boxplot(data=data, palette=['lightcoral', 'lightblue'])

# Add labels and title
plt.xlabel('Heart Disease')
plt.ylabel('BMI')
plt.title('Distribution of BMI by Heart Disease')

# Show the plot
plt.show()
```

### Findings
1. Age emerged as a significant factor, with a positive correlation observed between age and the risk of heart disease.
2. Other factors included high blood pressure, stroke, diabetes, high cholesterol levels, and smoking were also identified as significant risk factors for
heart disease.

### Recommendations
While the analysis provided valuable insights into the relationships between various factors and heart disease, it is crucial to note that correlations and trends alone do not establish causation. To gain a more comprehensive understanding, further analysis using advanced tools, such as linear regression or machine learning models, should be considered. These methods can help identify the most influential factors and
develop predictive models for assessing the risk of heart disease.

