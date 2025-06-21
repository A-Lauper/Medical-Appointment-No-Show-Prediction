# Medical Appointment No-Show Prediction

Final project for CST383: Introduction to Data Science, submitted by:
- Arielle Lauper (alauper@csumb.edu)
- Ichiro Miyasato (imiyasato@csumb.edu)
- Kelia Smith (kelismith@csumb.edu)
- Maria Imperatrice (mimperatrice@csumb.edu)

**Presentation Video Link**: https://drive.google.com/file/d/1Gw4fxL176nGfhDyLZWYB_bhxrAKD5d1I/view?usp=sharing

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
**Tools**: NumPy, pandas, scikit-learn, seaborn, matplotlib for data processing, modeling, and visualization.  
**Models**: 
- Baselines: Majority-class (all show), median-based (random prediction).  
- Supervised: K-Nearest Neighbors; Random Forest. 
- Unsupervised: K-means (clusters patients), Isolation Forest (detects outliers).  

**Justification**: Random Forest handles imbalanced data well; KNN is interpretable but less robust. K-means reveals patient patterns; Isolation Forest identifies high-risk outliers. K-means allowed categories to be compared again no-show, demonstrating how certain clusters are more proned to missed appointments. Isolation Forest was used an an alternative to KNN anomaly detection due to the size of the dataset, taking computational efficiency into account.       

### Results
The majority and median baseline has high accuracy but fails to identify no-shows. KNN performs moderately, while Random Forest excels, better identifying high-risk patients. Key predictors include past missed appointments and SMS reminders (per permutation importance). K-means identifies a high-risk cluster; anomalies from Isolation Forest show elevated no-show rates. The results guide clinics in prioritizing interventions for high-risk patients.

**Interpretation**:  
- **Accuracy**: Measures overall correctness, less reliable due to imbalance. (True Positive + True Negative) divided by Total Sample  
- **Precision**: Ensures efficient intervention targeting. (True Positive) divided by (True Positive + False Positive)  
- **Recall**: Captures high-risk patients, critical for impact. (True Positive) divided by (True Positive + False Negative)

### Discussion
The findings suggest clinics can use Random Forest to target high-risk patients, reducing no-shows and optimizing schedules. Past no-shows as a predictor align with behavioral studies, while SMS results indicate targeted reminders. K-means clustering was used to divide patients into relevant categories based on features. An average score was computed across these categories and compared against no-show. The clustering revealed certain patient groups, such as older high-need individuals and younger low-risk individuals, showed different behavioral risk patterns tied to attendance. Isolation Forest was applied within these clusters to identify anomalies—patients whose patterns deviate significantly from others in their group. Limitations include data imbalance and sparse Saturday records. Future work could involve tuning models or adding features (e.g., clinic distance). With more time, we may compare other features against each other instead of only no-shows; there could be more emphasis on numerical data rather than categorical.  

### Summary
Random Forest excels at predicting no-shows, with past missed appointments and SMS reminders as top predictors. Clustering and anomaly detection highlight high-risk groups, enabling clinics to improve efficiency through targeted interventions. 
The results for K-means clustering suggests that the behavioral category is the strongest differentiator across all clusters suggesting that intervention strategies should be focused on addressing these behaviors tied to these features. Isolation Forest was used to detect anomalies within each cluster, identifying patients that were not typical. It highlighted nearly 1,900 anomalies within the Older High-Need group, flagging these indiviudals for further analysis.   
As for what causes missed appointments, the answer is circular. Missed appointments cause missed appointments, but what causes the missed appointments in the first place? We can only conclude that for demographics and medical factors, there is weak correlation with missed appointments.
