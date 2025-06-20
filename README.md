# Medical-Appointment-No-Show-Prediction

Final project for CST383: Introduction to Data Science, submitted by:
- Arielle Lauper (alauper@csumb.edu)
- Ichiro Miyasato (imiyasato@csumb.edu)
- Kelia Smith (kelismith@csumb.edu)
- Maria Imperatrice (mimperatrice@csumb.edu)

### Introduction 
This project tackles the problem of missed medical appointments, which disrupt clinic operations and delay patient care. The research question is: can we predict if a patient will miss an appointment using demographic, medical, and scheduling data? The goal is to build a model to help clinics reduce no-shows, improving efficiency and resource use.

### Selection of Data 
**Source**: [Kaggle.com: Medical Appointment No Shows](https://www.kaggle.com/datasets/joniarroba/noshowappointments)
- Data Licence: [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
- Date Downloaded: June 3rd, 2025
  
**Characteristics**: Over 100,000 Brazilian clinic records, including age, gender, medical conditions (e.g., hypertension), SMS reminders, and no-show status. Imbalanced (~20% no-shows).  

**Munging**: Standardized column names, removed invalid ages, dropped irrelevant columns (e.g., neighbourhood).  

**Feature Engineering**: Created `days_between`, `day_of_week`, `past_missed`, `is_weekend`; standardized numerical features.

### Methods
**Tools**: NumPy, pandas, scikit-learn, seaborn, matplotlib.  
**Models**: 
- Supervised: Random Forest (ensemble, robust for imbalance), KNN (simple).  
- Unsupervised: K-means (clusters patients), Isolation Forest (detects outliers).  
- Baselines: Majority-class (all show), median-based (random prediction).  

**Justification**: Random Forest handles imbalanced data well; KNN is interpretable but less robust. K-means reveals patient patterns; Isolation Forest identifies high-risk outliers.  

**Metrics**: Accuracy (correct predictions), RMSE (error size).  

### Results
Random Forest outperformed KNN and baselines, achieving higher accuracy and lower RMSE, better identifying no-shows. Past missed appointments and SMS reminders were key predictors, per permutation importance. K-means clustering revealed three patient groups with varying no-show rates. Anomalies detected by Isolation Forest had higher no-show likelihoods. Accuracy is skewed by imbalance; RMSE shows model fit. These results answer the research question by identifying at-risk patients.

### Discussion
The findings suggest clinics can use Random Forest to target high-risk patients, reducing no-shows and optimizing schedules. Past no-shows as a predictor align with behavioral studies, while SMS results indicate targeted reminders. Limitations include data imbalance and sparse Saturday records. Future work could involve tuning models or adding features (e.g., clinic distance). With more time, we may compare other features against each other instead of only no-shows; there could be more emphasis on numerical data rather than categorical.

### Summary
Random Forest excels at predicting no-shows, with past missed appointments and SMS reminders as top predictors. Clustering and anomaly detection highlight high-risk groups, enabling clinics to improve efficiency through targeted interventions.  
As for what causes missed appointments, the answer is circular. Missed appointments cause missed appointments, but what causes the missed appointments in the first place? We can only conclude that for demographics and medical factors, there is weak correlation with missed appointments.
