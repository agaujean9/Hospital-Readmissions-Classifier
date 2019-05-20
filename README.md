## Hospital-Readmissions-Classifier

# Objective

Hospital readmission after an admitted patient is discharged is a high priority for hospitals. In total, Hospital Readmissions are one of the most costly episodes to treat, costing Medicare about $26 billion annually, with about $17 billion consisting of avoidable trips after discharge. The concern for Hospitals with readmission within 30 days centers around hospitals paying a penalty if an individual is "an readmitted to an acute care hospital within 30 days of discharge from the same or another acute care hospital."

For our project we thought it would be important if we could predict if an individual was likley to be readmitted within 30 days or not.The health care burden of hospitalized patients with diabetes (1 and 2) is substantial and only growing. As of today, around 9% of Americans have diabetes or prediabetes, according to a recent CDC report.A better understanding of the factors that lead to hospital readmissions could help decision makers understand potential ways to reduce early readmissions (within 30 days) and provide more efficient care for high risk patients. Based on the data that we had access too we addressed our problem as a classification problem.  We focused our project on attempting to predict whether a discharged diabetic patient will be readmitted into a hospital within 30 days (Target = 1)  or not (Target = 0).

# Data Collection

First, we collected diabetic patient data from 130 hospitals over a ten year span (1998-2008) from the UCI Machine Learning Database. This data included an indviduals patient records from that 10 year span with their identificaion encoded as a patient number. In addition, our dataset had a column containing our target variable (readmission <30 days) with respect to that patients most recent visit. 

# Exploratory Analysis and Dimensionality Reduction

However, at this point our data was still pretty sparse, in part because the primary and secondary diagnoses that were included for each of our patients consisted of countless diseases that was going to make it difficult to reduce the sparsity. In order to deal with this element of our data, my partner and I scraped IDC-10 codes and the corresponding category of disease, and used this to simplify each individuals primary and secondary ailments to one category of disease. 
Following this we ran Principal Component Analysis on our scaled continuous variables in order to reduce dimensionality even further. We were left with 6 principal components, with our cutoff meaning each component explains at least .075 of the observed variance. 

Unsurprisingly, as is often the case with medical classification datasets we were left with a class imbalance. Where our readmitted patients accounted for only 11% of our dataset. However, because of our enormous dataset we had no need to create sythetic data we just undersampled the class of individuals who were not readmitted. And used a limited dataset of 10,625 samples. Still plenty large enough to conduct the classification algorithm that we had in mind. 

# Model Tuning
We started with a baseline logistic regression model just to see if there was any predictive value in some of the variables that we engineered. This resulted in a train and test recall score of .53 and .55 respectively. We chose to look at recall as a metric becauase given the state of our problem our fundamental goal was to be able to identify anyone who might be at risk for readmission within 30 days. Even if we find out our model is biased toward Type I error we would prefer that to the alternative of our model predicting an individual should be released just to have him readdmitted within 30 days. 

Following Logistic Regression we ran a number of other classification models, including KNN, Random Forest, XGBoost, and Stochiastic Gradient Descent. Taking time to fine tune each model using GridSearchCV. After a number of iterations our best performing model was our XG Boost which received a 63% on the train set.

# Conclusion

This was not the most ideal score but given the predictors that we had at our disposal it proved to be a decent success with respect to the objective that we were classifying. 


