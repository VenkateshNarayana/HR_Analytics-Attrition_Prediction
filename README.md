# HR-Analytics - Attrition Prediction
<p align="center">
  <img width="460" height="300" src="HR-EmployeeAtrrition/images/HRAnalytics.jpg">
</p>


## INTRODUCTION
My client is a large MNC and they have 9 broad verticals across the organisation. One of the problem my client is facing is around identifying the people who are at risk of "atrrition".
Hence,the company needs a help in identifying the probable candidates at a particular checkpoint so that they can take preventive measures to mitigate the "attrition risks. Below is a table showing names of all the columns and their description. 
Below is a table showing names of all the columns and their description.

## DATA
| Column Name              | Description                                                                     |
| -------------            | -------------                                                                   | 
| Age                      | Age  Details                                                                    |
| Attrition                | Attrition  Details                                                              |
| BusinessTravel           | BusinessTravel  Details                                                         |
| DailyRate                | DailyRate  Details                                                              |
| Department               | Department Details                                                              |
| DistanceFromHome         | DistanceFromHome  Details                                                       |
| Education                | Education  Details                                                              |
| EducationField           | EducationField  Details                                                         |
| EmployeeCount            | EmployeeCount Details                                                           |
| EmployeeNumber           | EmployeeNumber  Details                                                         |
| EnvironmentSatisfaction  | EnvironmentSatisfaction  Details                                                |
| Gender                   | Gender  Details                                                                 |
| HourlyRate               | HourlyRate Details                                                              |
| JobInvolvement           | JobInvolvement  Details                                                         |
| JobLevel                 | JobLevel  Details                                                               |
| JobRole                  | JobRole  Details                                                                |
| JobSatisfaction          | JobSatisfaction Details                                                         |
| MaritalStatus            | MaritalStatus  Details                                                          |
| MonthlyIncome            | MonthlyIncome  Details                                                          |
| MonthlyRate              | MonthlyRate  Details                                                            |
| NumCompaniesWorked       | NumCompaniesWorked Details                                                      |
| Over18                   | Over18  Details                                                                 |
| OverTime                 | OverTime  Details                                                               |
| PercentSalaryHike        | PercentSalaryHike  Details                                                      |
| PerformanceRating        | PerformanceRating Details                                                       |
| RelationshipSatisfaction | RelationshipSatisfaction  Details                                               |
| StandardHours            | StandardHours  Details                                                          |
| StockOptionLevel         | StockOptionLevel Details                                                        |
| TotalWorkingYears        | TotalWorkingYears  Details                                                      |
| TrainingTimesLastYear    | TrainingTimesLastYear  Details                                                  |
| WorkLifeBalance          | WorkLifeBalance Details                                                         |
| YearsAtCompany           | YearsAtCompany  Details                                                         |
| YearsInCurrentRole       | YearsInCurrentRole  Details                                                     |
| YearsSinceLastPromotion  | YearsSinceLastPromotion Details                                                 |
| YearsWithCurrManager     | YearsWithCurrManager Details                                                    |


## PROJECT ANALYSIS
| Description | Analysis |
| --- | --- |
| Red wine  | ![image.png](images/redwinedataset.png) |
| White wine | ![image.png](images/whitewinedataset.png) |


### CONCLUSION

|     | Models Analysed |
| --- | ---             |
| Model Results                  | ![image.jpg](images/Models.jpg) |
| Model-Cross Validation Results | ![image.jpg](images/CrossValidationResults.png) |
| Model-Grid Search Results      | ![image.jpg](images/GridSearchResults.png) |

#### Observation
##### Based on the data available we try the following approaches to see if the model built on these gives a good accuracy.
- Check a Model which doesnt includes type information, keep the outliers, doesnt scale data nor add any weights (due to imbalance data) and see if the KNN, Logistic Regression or Decision Tree provide good accuracy.
- Check if we add weights but ignore type, keep outliers and use unscaled data.
- Check if accuracy improves if we add type, remove outliers, scale data and add weights for predicting the quality 

After trying all the above it was observed that accuracy could not go beyond 61% even after adding type, removing outliers, standardised data to scale and adding weights. 

The approach is to see if we can bin the class "quality" from 0-10 to 3 major categories 0-2 [poor] ,3-6 [good] and 7-10 [excellent]. and see if the same Model is able to predict the class "quality" now more accurately.

##### For the new class (with 3 category) we found that by adding weights , standardised scale data ,including type the accuracy increased and the best was for KNN  88% for n = 16.

And, The best score for Logistic regression and Decision Tree was model 4 with 82% and Model 8A with 84% respectively.

##### Using cross validation with the new class (with 3 category) we found that accuracy increased to 96% for KNN , Random Forrest and Logistic Regression

![image.jpg](images/CrossValidationResults.png) 

And, Using Grid Search we found that to get the accuracy of 96% for KNN and Logistic Regression, we use KNN with parameters as n_estimator :1 6, p=2, algorithm=auto, metric=minkowski and weights=uniform.

![image.jpg](images/GridSearchFinalResults.png) 
#### Conclusion
##### KNN provides the highest accuracy of 96% with grid search and we use the best parameters as below:
-n_estimator :16
-p=2
-algorithm=auto
-metric=minkowski
-weights=uniform.
.


[Jupyter Notebook](.HR-EmployeeAtrrition/EDA_ModelEvaluation_Report/HRAnalytics_AttritionPrediction_V5.ipynb)

