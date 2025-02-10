# **Surface Classification Using Machine Learning**  

This task focuses on **classifying different surface types** using machine learning models. It involves **data preprocessing, feature selection, outlier treatment, and model training**, including hyperparameter tuning for optimal performance.  

---

## **Project Overview**
The dataset comprises accelerometer readings from different body parts, with **seven surface classes**:  
- **BnkL**, **BnkR** (Bank left and right)  
- **CS** (Concrete Surface)  
- **FE** (Flat Earth)  
- **GR** (Grass)  
- **SlpD**, **SlpU** (Slope Down and Up)  

The objective is to train machine learning models that can accurately classify these surfaces based on the provided IMU sensor data.  

---

## **Project Structure**
```bash
Surface-Classification-Project/
│── data/
│   ├── Merged_Data_OneHotEncoded_numeric.csv
│   ├── Merged_Data_OneHotEncoded.csv
│   ├── Merged_Data_Selected_Features_numeric.csv
│   ├── Merged_Data_Selected_Features.csv
│   ├── Merged_Dataset_OneHotEncoded_numeric_IQR_Clipped.csv
│   ├── Merged_Dataset.csv
│   ├── Shank_4_cycle.csv
│   ├── Shank_4_cycle.xlsx
│   ├── Thigh_4_cycle.csv
│   ├── Thigh_4_cycle.xlsx
│   ├── Trunk_4_cycle.csv
│   ├── Trunk_4_cycle.xlsx
│── notebooks/
│   ├── data_exploration.ipynb
│   ├── model_TreatedOutliers.ipynb
│   ├── model_WithFeatureSelection.ipynb
│   ├── model.ipynb
│── requirements.txt
│── README.md

```

---

## **Pre-processing**
- Merging datasets from different sensors
- One-hot encoding categorical labels
- Feature selection via correlation analysis
- Outlier treatment using IQR clipping

---

## **Tested Datasets**
Three versions of the dataset were tested:  
- `Merged_Data_OneHotEncoded_numeric.csv` - **All features, outliers included**  
- `Merged_Data_Selected_Features_Numeric.csv` - **Redundant features removed, outliers included**  
- `Merged_Dataset_OneHotEncoded_Numeric_IQR_Clipped.csv` - **All features, outliers treated**  

---

## **Model Training & Evaluation**
Models Tested:
- Random Forest (RF)
- K-Nearest Neighbors (KNN)
- Hyperparameter tuning for RF 


### **Hyperparameter Tuning**
Grid search was applied to optimize model performance, particularly for **Random Forest** (n_estimators, max_depth, min_samples_split) 

---

## **Results & Discussion**  

### **Key Findings**  
- **Feature Selection:** Had minimal impact on model performance.  
- **Outlier Treatment:** Slightly reduced accuracy, suggesting outliers contained useful information.  
- **Model Comparison:** KNN consistently outperformed Random Forest (RF).  
- **Hyperparameter Tuning:** Improved RF’s precision and recall, making it more competitive.  
- **Best Performance:** KNN achieved the highest accuracy (93.98%) on the **original dataset**.  

---

### **Model Performance Evaluation**  

| **Dataset**           | **Model**    | **Accuracy** | **Precision** | **Recall** | **F1 Score** |
|----------------------|-------------|------------|------------|--------|---------|
| **Original**        | RF          | 81.12%     | 46.22%     | 99.08% | 62.76%  |
|                    | KNN         | **93.98%** | 96.04%     | 92.26% | **94.06%** |
|                    | Tuned RF    | 87.51%     | **99.12%** | 83.92% | 90.56%  |
| **Selected Features** | RF          | 78.95%     | 43.49%     | **99.12%** | 60.15%  |
|                    | KNN         | 93.94%     | 96.06%     | 92.24% | 94.04%  |
|                    | Tuned RF    | 87.18%     | 99.03%     | 83.63% | 90.35%  |
| **Treated Outliers** | RF          | 81.04%     | 46.10%     | 99.06% | 62.64%  |
|                    | KNN         | 93.07%     | 95.56%     | 91.15% | 93.23%  |
|                    | Tuned RF    | 87.59%     | 99.03%     | 84.21% | 90.74%  |

---

### **Key Observations**  
- **KNN consistently achieved the best performance**, indicating a well-separated feature space.  
- **Tuning significantly improved RF performance**, especially in precision and recall.  
- **Feature selection had little impact**, suggesting the original features were already well-optimized.  
- **Outlier treatment slightly reduced accuracy**, meaning outliers held valuable information.  

---

## **Conclusion & Future Work**  
- **KNN is the most effective model for this dataset** but should be tested on new data for robustness.  
- **Hyperparameter tuning greatly improved RF**, making it a strong alternative to KNN.  
- **Further improvements include:**  
  - **Dataset Balancing** to reduce bias toward frequent surface types.  
  - **Automatic Feature Selection** to improve efficiency without accuracy loss.  
  - **Exploring Deep Learning** for potentially better generalization.  
