# Cognitive Load Detection from EEG + GSR

## Overview
This project focuses on **classifying task difficulty or cognitive load** using physiological signals: EEG (brainwaves) and GSR (skin conductance). The objective is to detect cognitive load levels (Low, Medium, High) for participants performing tasks, using machine learning and deep learning approaches.

---

## Dataset

### Targets
- **Task difficulty labels** from experimental logs  
- **NASA-TLX scores** mapped into categories: Low, Medium, High cognitive load

### Inputs
1. **EEG.csv**: Brainwave features across frequency bands  
   - Delta, Theta, Alpha, Beta, Gamma  
2. **GSR.csv**: Skin conductance / resistance data  

### Data Organization
- Per-task samples: Each row corresponds to one trial of one participant.  
- Features are extracted from EEG + GSR over the task window `[routineStart, routineEnd]`.  
- Labels correspond to cognitive load class (binary or 3-class).  

---

## Preprocessing Pipeline

1. **Synchronize Timestamps**  
   - Slice EEG & GSR data according to task windows  
   - Align modalities, resample if needed  

2. **Feature Engineering**  
   - **EEG features**:  
     - Mean and variance of Delta, Theta, Alpha, Beta bands  
     - Ratios like Theta/Alpha, Theta/Beta (linked to workload)  
     - Power spectral entropy, bandpower slope  
   - **GSR features**:  
     - Mean skin conductance level  
     - Peak frequency of phasic responses  
     - Number of skin conductance responses (SCRs) during task  
     - Rise and recovery times  

3. **Label Encoding**  
   - Binary: Low Load = 0, High Load = 1  
   - Multi-class: Low = 0, Medium = 1, High = 2  

4. **Scaling & Cleaning**  
   - Normalize features across participants  
   - Handle missing EEG/GSR windows using interpolation  

---

## Modeling Approaches

### Baseline ML Models
- Logistic Regression, SVM  
- Random Forest  
- Gradient Boosting: XGBoost, LightGBM, CatBoost  
- Evaluation metrics: Accuracy, F1-score, ROC-AUC (binary), Macro-F1 (multi-class)  

### Fusion Strategies (EEG + GSR)
- **Early Fusion**: Concatenate EEG and GSR features and train a single classifier  
- **Late Fusion**: Train separate EEG and GSR models → combine outputs via meta-classifier  

### Advanced Deep Learning
- **CNN**: Temporal filters on EEG + GSR segments  
- **BiLSTM**: Sequence modeling of physiological changes  
- **CNN-LSTM**: Hybrid approach  
- **Transformer-based encoders** for multimodal attention  

---

## Evaluation & Interpretability

- Metrics: Accuracy, Precision, Recall, F1 (macro for multi-class), Confusion Matrix  
- Interpretability:  
  - SHAP values for engineered features  
  - EEG frequency-band importance (Theta, Alpha ratios)  
  - GSR peak counts vs load levels  
  - Attention weights if transformer models are used  

---

## Experimentation & Improvements

- Compare **binary (Low vs High load)** vs **3-class (Low/Medium/High)** classification  
- Test **personalized models** (per participant) vs **generalized models**  
- Include temporal derivatives (EEG bandpower slope, GSR slope)  
- Explore **multimodal attention networks** for EEG+GSR fusion  
- Augment data using **sliding windows** for time-series deep learning  

---

## References
- NASA-TLX: [https://humansystems.arc.nasa.gov/groups/TLX/](https://humansystems.arc.nasa.gov/groups/TLX/)  
- EEG and Cognitive Load Research: Theta/Alpha ratios, bandpower slope, etc.  
- GSR features for workload analysis: peak frequency, SCR count  

---

## Author
- **Group_ID T1_G29 | Group_Name Mavericks_2**   
