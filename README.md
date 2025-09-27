# Cognitive Load Detection from EEG + GSR
---
## Model Evaluation

### Machine Learning Models (Participant 1)
| Model | Accuracy | Macro-F1 | 
|-------|---------|----------|
| Tuned GradientBoostingClassifier | 0.875 | 0.841 |
| Random Forest | 0.875 | 0.841 |
| SVM | 1.000 | 1.000 |
| Logistic Regression | 1.000 | 1.000 |

> Notes: Perfect scores for SVM & Logistic Regression likely due to small test set size (8 samples).

### ML Models Evaluation Across Participants 1–38 (5-fold CV)
#### Logistic Regression
- Macro-F1: 0.347 ± 0.021  
- Accuracy: 0.351 ± 0.020  
- ROC-AUC: 0.525 ± 0.015  

#### SVM
- Macro-F1: 0.366 ± 0.027  
- Accuracy: 0.371 ± 0.028  
- ROC-AUC: 0.558 ± 0.028  

#### Random Forest
- Macro-F1: 0.524 ± 0.024  
- Accuracy: 0.524 ± 0.024  
- ROC-AUC: 0.697 ± 0.019  

#### XGBoost
- Macro-F1: 0.442 ± 0.023  
- Accuracy: 0.443 ± 0.023  
- ROC-AUC: 0.613 ± 0.018  

#### LightGBM
- Macro-F1: 0.492 ± 0.030  
- Accuracy: 0.493 ± 0.030  
- ROC-AUC: 0.663 ± 0.020  

#### CatBoost
- Macro-F1: 0.470 ± 0.030  
- Accuracy: 0.472 ± 0.030  
- ROC-AUC: 0.644 ± 0.022  
---
### Deep Learning Models (Participants 1–38)
| Model | Accuracy |
|-------|----------|
| CNN | 42.48% |
| CNN-BiLSTM Hybrid (feature data) | 42.48% |
| CNN-LSTM | 42.48% |
| Transformer (feature data) | 42.48% |
| Highly Tuned CNN-BiLSTM (feature data) | 41.35% |
---
## Author
- **Group_ID T1_G29 | Group_Name Mavericks_2**   
