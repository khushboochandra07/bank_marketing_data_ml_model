## feature-determining-car-prices

Vehicle data analysis repository investigates and creates independent analysis to provide clear recommendation to my client-a used car dealreship-as to what consumers value in a car using CRISP-DM framework. vehicles.csv data from kaggle contains information of 426K cars for the analysis. 

## Jupyter Notebook

Use the [jupyternotebook\1_bank_campaign_success_model_analysis.ipynb](https://github.com/khushboochandra07/vehicle_data_analysis/blob/main/jupyternotebook/1_bank_campaign_success_model_analysis.ipynb) to look at the results and findings

## CRISP_DM Framework

![CRISP-DM Framework](/images/crispdm.png)

### **Business Understanding**  

*   Data is from a Portuguese banking institution and is a collection of the results of multiple marketing campaigns.
*   The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.
*   The classification goal is to predict if the client will subscribe a term deposit (variable y).


### **Data Understanding**  

The vehicle data provided as part of the analysis has data about sale price from few years for various cars, vans, trucks for preowned vehicles. It also contains columns columns like condtion, odometer reading, drive and fuel. This data directly ties to the ask from the client.

*   Size of original data is 41188 rows and 12 columns
*   Columns are not missing any data
*   Duration column seems to be redundant and doesn't add so much value to the study.
*   Categorical columns - 'job', 'marital', 'education', 'default', 'housing', 'loan','poutcome'
*   Numerical columns - 'age','campaign','pdays','previous'
*   Target column 'y' holds binary yes/no value


### **Data Preparation**  

Categorical columns have finite values so OneHotEncoder applied for encoding categorical columns. Standard scaler applied to numerical columns. 



Visualization

**Campaign Success Count by Categorical Variables**
![alt text](/images/Campaign_success.png)

**Correlation Matrix for features**

![alt text](/images/correlation.png)

Conclusion from the visualization and correlation matrix;
*   People with administrative jobs and no defaults on their credit exclusively are highly likely to enroll.
*   Married individuals and individuals with university degree have higher chances of enrolling in the term deposit.
*   Housing doesn't seem to indicate the success of term deposit.
*   euribor3m has high postive correlation with nr.employed, emp.var.rate and cons.conf.idx.
*   previos is negatively correlated to nr.employed, emp.var.rate, pdays and euribor3m

### **Modeling**  

**Results from simple Model**

![alt text](/images/simple_coeff.png)
![alt text](/images/simple_classification.png)

Confusion Matrix:
[[7229   81]
 [ 751  177]]

**Model comparison results**

*   SVM is the slowest 
*   KNN trains fastet
*   Logistic Regression has highest accuracy
![alt text](/images/model_comp.png)

Cross validation results:

              Model CV Accuracy Std Dev
Logistic Regression      0.8977  0.0018
                KNN      0.8900  0.0014
      Decision Tree      0.8412  0.0029
                SVM      0.8977  0.0022

![alt text](/images/model_accuracy.png)

![alt text](/images/cross_validation.png)

**Improving the model**

Best params for each model:
![alt text](/images/hyperparameter_tuning.png)


**Final Recommendation**
*   Based on simple model and classifier comparison of KNN, SVM, Logistic Regresion and Decision tree best performance is of Logistic Regression. Most table based on CV and std deviation is KNN.
*   After hyperparameter tuning, we notice that KNN performs the best with Model Parameters: {'algorithm': 'auto', 'leaf_size': 30, 'metric': 'minkowski', 'metric_params': None, 'n_jobs': None, 'n_neighbors': 5, 'p': 2, 'weights': 'uniform'}

# Copyright (c) Khushboo Chandra.