# Tracking User Engagement with SQL, Excel, and Python

This repository contains the solution to the **Tracking User Engagement with SQL, Excel, and Python** project from the 365 Data Science Career Track (https://learn.365datascience.com/projects/tracking-user-engagement-with-sql-excel-and-python/?tab=description). The objective of the project is to analyze whether the introduction of new features (career tracks, exams, expanded course library) on a learning platform increased student engagement between Q2 2021 and Q2 2022.


## Table of Contents
- [Introduction](#Introduction)
- [Getting Started](#getting-started)
- [Hypothesis](#hypothesis)
- [Tools and Libraries Used](#tools-and-libraries-used)
- [Methodology](#methodology)
  - [Part 1: Data Preparation with SQL – Creating a View](#part-1-data-preparation-with-sql--creating-a-view)
  - [Part 2: Data Preparation with SQL – Splitting Into Periods](#part-2-data-preparation-with-sql--splitting-into-periods)
  - [Part 3: Data Preparation with SQL – Certificates Issued](#part-3-data-preparation-with-sql--certificates-issued)
  - [Part 4: Data Preprocessing with Python – Removing Outliers](#part-4-data-preprocessing-with-python--removing-outliers)
  - [Part 5: Data Analysis with Excel – Hypothesis Testing](#part-5-data-analysis-with-excel--hypothesis-testing)
  - [Part 6: Data Analysis with Excel – Correlation Coefficients](#part-6-data-analysis-with-excel--correlation-coefficients)
  - [Part 7: Dependencies and Probabilities](#part-7-dependencies-and-probabilities)
  - [Part 8: Data Prediction with Python](#part-8-data-prediction-with-python)
- [Conclusion](#conclusion)


---

## Introduction

Welcome to the **Tracking User Engagement with SQL, Excel, and Python** project! from 365datascience projects. This project is designed to assess how new features (such as career tracks, exams, and expanded course offerings) released by the platform in late 2021 affected student engagement in the first half of 2022.

We will analyze data from various sources using SQL, Excel, and Python to compare student activity between Q2 2021 and Q2 2022 based on data of their platform, investigate hypotheses about platform engagement, and generate actionable insights.

---

## Getting Started

To begin working with this project, follow the instructions below:

### Prerequisites:
- **Python 3.x**: Required for data analysis and predictive modeling.
- **Excel 2007 (or later)**: Needed for hypothesis testing and calculating correlation coefficients.
- **MySQL Workbench 8.0 (or later)**: Required for working with the provided SQL database containing student engagement data.

### Install Required Libraries:
1. Clone the repository:
   ```bash
   git clone https://github.com/NirajanKhadka/Tracking-User-Engagement-SQL_EXCEL_PYTHON.git
   ```

2. Navigate to the project directory:
```bash
cd your-repository-name

```
3. Install Python dependencies:
```python
pip install pandas matplotlib statsmodels scikit-learn seaborn

```
4. Set up SQL Database:

Import the provided SQL database into MySQL Workbench or your preferred SQL platform.
Connect to the database and verify the tables for student engagement data.

## Tools and Libraries Used

- **SQL**: To query and organize data from the database.
- **Python**:
  - `pandas`: For data manipulation and cleaning.
  - `matplotlib`, `seaborn`: For data visualization.
  - `statsmodels`: For hypothesis testing and statistical analysis.
  - `scikit-learn`: For machine learning (if needed).
- **Excel**: For statistical analysis, data visualization, and summarizing results.

---

## Hypothesis

We conducted hypothesis testing to determine if student engagement in Q2 2022 was significantly higher than in Q2 2021. The null hypothesis and alternative hypothesis were defined as follows

**Null Hypothesis (H₀)**: There is no significant difference in engagement between Q2 2021 and Q2 2022.
**Alternative Hypothesis (H₁)**: Engagement in Q2 2022 is higher than in Q2 2021.
---



## Methodology

The project is broken down into the following key parts. Each part follows a logical flow, from data extraction to analysis and prediction.

### Part 1: Data Preparation with SQL – Creating a View

#### **What’s Happening**:
In this step, we extract key data from the platform's database using SQL. We then create views that combine relevant tables for easy access and streamlined analysis.

#### **Why We Do This**:
Using SQL views allows us to efficiently filter and prepare data for analysis, reducing the complexity of queries in later steps.

#### **Key SQL Operations**:
- Extract data on student purchases, engagement, and certificate issuance.
- Create views to combine these data points.

<p align="center">
<img src="images/view_sql.png>
</p>

---

### Part 2: Data Preparation with SQL – Splitting Into Periods

#### **What’s Happening**:
We split the data into two time periods: Q2 2021 (pre-release of new features) and Q2 2022 (post-release). This division helps us compare engagement metrics before and after the introduction of the new features.

#### **Why We Do This**:
By analyzing the data in these distinct periods, we can assess how engagement changed due to the new features.

#### **SQL Queries**:
- Filter engagement data by periods.
- Aggregate data for Q2 2021 and Q2 2022.

<p align ="center">
<img src = "images/sql_periods.png>
</p>

---

### Part 3: Data Preparation with SQL – Certificates Issued

#### **What’s Happening**:
We analyze the issuance of certificates for students who completed courses or exams during Q2 2021 and Q2 2022. This will serve as a key metric for student engagement.

#### **Why We Do This**:
Certificates issued can indicate the level of student achievement and engagement. Comparing this metric over two periods helps us understand whether students are more engaged in the new learning environment.

#### **SQL Operations**:
- Extract certificate issuance data.
- Compare across Q2 2021 and Q2 2022.

<p align ="center">
<img src = "images/certificate_sql.png>
</p>
---

### Part 4: Data Preprocessing with Python – Removing Outliers

#### **What’s Happening**:
Outliers in the data can skew analysis and lead to inaccurate conclusions. Using Python, we identify and remove outliers from the dataset to ensure the analysis reflects the true engagement patterns.

#### **Why We Do This**:
Outliers can distort statistical tests and regression models, so it's important to remove them before proceeding with further analysis.

<p align ="center">
<img src = "images/Before_outlier_removal.png>
</p>

#### **Python Code**:

```python
#now lets filter the data
minutes_watched_2021_paid=minutes_watched_2021_paid[minutes_watched_2021_paid['minutes_watched']<percentile_99_2021_paid]
minutes_watched_2021_free=minutes_watched_2021_free[minutes_watched_2021_free['minutes_watched']<percentile_99_2021_free]
minutes_watched_2022_paid=minutes_watched_2022_paid[minutes_watched_2022_paid['minutes_watched']<percentile_99_2022_paid]
minutes_watched_2022_free=minutes_watched_2022_free[minutes_watched_2022_free['minutes_watched']<percentile_99_2022_free]
```

<p align ="center">
<img src = "images/After_outlier_removal.png>
</p>

### Part 5: Data Analysis with Excel – Hypothesis Testing

#### What’s Happening:
In this part, we perform hypothesis testing in Excel to verify whether there’s a statistically significant difference in student engagement between Q2 2021 and Q2 2022.

#### Why We Do This:
Hypothesis testing helps us objectively determine whether the observed differences in engagement are due to the new features or if they occurred by chance. By analyzing this, we can make data-driven decisions about whether the new platform features were effective in increasing student engagement.

#### Steps:
1. **Set Null and Alternative Hypotheses**:
   - **Null Hypothesis (H0)**: There is no significant difference in engagement between Q2 2021 and Q2 2022.
   - **Alternative Hypothesis (H1)**: There is a significant difference in engagement between Q2 2021 and Q2 2022.

2. **Perform t-test or ANOVA (as appropriate)**:
   - In Excel, we can use the `T.TEST` function for comparing the means of two groups.
   - For a t-test, we will compare engagement data from Q2 2021 and Q2 2022 to assess whether the difference in means is statistically significant.

3. **Interpret the p-value**:
   - If the p-value is less than 0.05 (commonly used threshold), we reject the null hypothesis and conclude that the difference in engagement between the two periods is statistically significant.
   - If the p-value is greater than 0.05, we fail to reject the null hypothesis and conclude that the difference is not statistically significant.

<p align ="center">
<img src = "images/Summary_stat.png>
</p>


<p align ="center">
<img src = "images/Hypo_testing.png>
</p>


### Part 6: Data Analysis with Excel – Correlation Coefficients

#### What’s Happening:
In this part, we calculate the correlation coefficients between different variables, such as time watched and the issuance of certificates, to understand the relationships between engagement metrics.

#### Why We Do This:
Correlation analysis helps us identify patterns or relationships between different aspects of student activity. By understanding these relationships, we can determine which factors are most strongly associated with student engagement. This step is crucial for uncovering hidden insights and optimizing platform features to maximize student interaction.

#### Steps:
1. **Choose the Variables for Correlation**:
   - For this analysis, we focus on variables like the **time watched** by students and the **issuance of certificates**.
   - Other possible variables include the number of courses taken, exam scores, and career track enrollments.

2. **Calculate Pearson’s or Spearman’s Correlation**:
   - **Pearson’s correlation** is used for linear relationships between continuous variables.

3. **Interpret the Correlation Coefficient**:
   - The correlation coefficient (r) ranges from -1 to 1:
     - **r = 1**: Perfect positive correlation.
     - **r = -1**: Perfect negative correlation.
     - **r = 0**: No correlation.
   - Values closer to 1 or -1 indicate a stronger relationship, while values near 0 suggest no relationship.

4. **Visualize the Correlation Matrix**:
   - Visualizing the correlation matrix helps identify patterns easily. You can use a heatmap to display the strength of the correlations between different variables.

#### Excel Steps:
1. **Prepare the Data**:
   - Ensure that you have your data in a tabular format, with each column representing a variable (e.g., Time Watched, Certificate Issued, Number of Courses, etc.).

2. **Calculate the Correlation**:
   - In Excel, use the `=CORREL(array1, array2)` function for Pearson’s correlation between two sets of data.
   - For example, to calculate the correlation between time watched (Column A) and certificate issuance (Column B):
     ```excel
     =CORREL(A2:A100, B2:B100)
     ```

3. **Interpret the Results**:
   - A positive correlation between time watched and certificates issued suggests that students who engage more with the platform (watching more content) are more likely to complete courses and earn certificates.
   - A weak or negative correlation may suggest that other factors, like course difficulty or engagement in exams, play a role in certificate issuance.

<p align ="center">
<img src = "images/Hypo_testing.png>
</p>

### Part 7: Dependencies and Probabilities

#### What’s Happening:
In this part, we use probability theory to assess dependencies between different variables, such as the likelihood of a student watching a course if they are registered for a career track. We will explore how one event impacts the probability of another event occurring, which can be valuable for making predictions or guiding platform features.

#### Why We Do This:
Understanding dependencies and probabilities helps us assess the effect of one variable on another. This is important because certain actions or behaviors may be more likely under specific conditions. By understanding these dependencies, we can optimize features and improve student engagement through targeted strategies. Probability theory provides a foundation for predictive modeling and decision-making.

#### Steps:
1. **Define the Problem**:
   - For this analysis, we focus on determining the probability of students watching a course in Q2 2022 given they have enrolled in a career track.
   - This helps to understand whether career track enrollment influences engagement, as we hypothesize that students engaged in career tracks may have higher course completion rates.

2. **Apply the Conditional Probability Formula**:
   - We use **conditional probability** to assess how the probability of one event (course watched) changes given the occurrence of another event (career track enrollment).
   - The formula for conditional probability is:
     \[
     P(A | B) = \frac{P(A \cap B)}{P(B)}
     \]
     Where:
     - \( P(A | B) \) is the probability of event A (watching a course) occurring given event B (being enrolled in a career track).
     - \( P(A \cap B) \) is the probability that both events A and B occur.
     - \( P(B) \) is the probability of event B (enrollment in a career track).

3. **Calculate Probabilities in Python**:
   - First, determine the total number of students who watched a course in Q2 2022 and the total number of students enrolled in career tracks using SQL.
   - Then, determine how many students were both enrolled in a career track and watched a course.
   - Use the formula to calculate the conditional probability of a student watching a course given they are enrolled in a career track.

<p align ="center">
<img src = "images/prob.png>
</p>

### Part 8: Data Prediction with Python

#### What’s Happening:
In this final part of the project, we apply predictive modeling to forecast student engagement in the future based on historical data. The goal is to predict which students are likely to engage with the platform in the coming months. This allows for better decision-making and more targeted strategies to enhance student engagement and retention.

#### Why We Do This:
Predictive modeling enables us to anticipate future trends and behavior based on existing data. By predicting student engagement, we can make informed decisions about course offerings, platform features, and marketing strategies. It allows the team to proactively address engagement issues before they arise.

#### Steps:
1. **Define the Prediction Problem**:
   - The objective is to predict student engagement, measured by the number of courses watched, in the upcoming months (e.g., Q3 2022).
   - We need to decide on the appropriate model based on the target variable (in this case, a continuous variable for engagement).

2. **Data Preprocessing for Prediction**:
   - **Missing Value Handling**: Ensure that missing data is properly handled, either by filling in missing values (e.g., using the mean or median) or by removing rows/columns with too much missing data.

3. **Choosing the Model**:
   - For predicting a continuous variable like course engagement, a **regression model** (e.g., linear regression, decision trees, or random forests) is appropriate.
   - We choose **Linear Regression** here.


4. **Model Training**:
   - We split the dataset into training and testing sets (e.g., 80% for training, 20% for testing).
   - The training data is used to teach the model how to predict student engagement.
   - The model is trained using the chosen algorithm (Random Forest Regressor).

5. **Model Evaluation**:
   - After training, the model is evaluated on the testing set.
   - We use metrics such as **Mean Absolute Error (MAE)** to assess the model’s accuracy.
   
6. **Predicting Engagement**:
   - Using the trained model, we make predictions for future student engagement based on the input features.
   - These predictions will help determine which students are more likely to engage and which may require intervention or targeted features.

<p align ="center">
<img src = "images/python.png>
</p>

### Conclusion

The data analysis of student engagement over two quarters (Q2 2021 and Q2 2022) reveals key insights regarding how engagement varies between free-plan and paid-plan students.

#### Key Findings:
1. **Engagement Differences**:
   - **Free-Plan Students**: While there are more non-paying students, the engagement (measured in minutes watched) is relatively low compared to paid subscribers. In Q2 2021, the average engagement for free-plan students was 14.21 minutes, and in Q2 2022, it increased slightly to 16.04 minutes.
   - **Paid-Plan Students**: Paid subscribers show significantly higher engagement. In Q2 2021, the average engagement was 360.10 minutes, but by Q2 2022, this dropped to 292.22 minutes. Despite the increase in non-paying student engagement, the paid-plan students saw a decrease in engagement over the year.

2. **Statistical Testing**:
   - **Hypothesis Testing**: The null hypothesis stated that engagement in Q2 2021 is greater than or equal to that in Q2 2022. However, after performing the t-test:
     - For **free-plan students**, the t-statistic was -3.95, which is less than the critical value of 1.645, leading to the rejection of the null hypothesis. This indicates that engagement in Q2 2021 is significantly lower than in Q2 2022 for non-paying students.
     - For **paid-plan students**, the t-statistic was 5.16, which is greater than the critical value of 1.645, suggesting that there is no significant decrease in engagement for paid subscribers between the two quarters, meaning we fail to reject the null hypothesis for this group.

3. **Correlation Analysis**:
   - A positive correlation coefficient of **0.566** was observed, indicating that as one variable (e.g., time spent watching videos) increases, the other variable (e.g., engagement or activity) also tends to increase. This suggests that the more students engage with the platform, the higher their overall activity.

4. **Engagement Distribution**:
   - Both the mean and median engagement times differed significantly between the two groups and over time, with distributions being skewed. This indicates variability in how different students engage with the platform, with a substantial number of students showing low engagement while others exhibit much higher engagement.

#### Implications:
- **For Non-Paying Students**: The data shows that the introduction of new features led to an increase in engagement, although this group still exhibits lower overall engagement than paid subscribers. Targeted interventions could further improve retention and engagement in this group.
- **For Paid Subscribers**: While paid-plan students were initially more engaged, the decrease in their engagement from Q2 2021 to Q2 2022 warrants further investigation. It suggests that the new features may not have had the desired effect, or there could be other factors influencing engagement. This could be an area for further analysis, such as identifying content or features that may be driving decreased usage.

#### Conclusion:
The overall findings highlight a positive impact of the new features on free-plan students but show a decline in engagement for paid subscribers. The rejection of the null hypothesis for free-plan students and the failure to reject it for paid-plan students suggests that while the new features were beneficial for non-subscribers, they might not have been as effective for paid subscribers. 

Moving forward, **future work** should focus on exploring why paid subscribers’ engagement decreased and investigating other possible factors, such as content relevance or the user interface, that could be optimized to boost engagement in this group.


