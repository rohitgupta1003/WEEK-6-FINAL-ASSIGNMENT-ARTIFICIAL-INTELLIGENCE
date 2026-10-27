# Week 6 Final Project - Breast Cancer Prediction using Machine Learning

This is my final project for the **Artificial Intelligence Internship (Week 6)**.
I built a machine learning model that predicts whether a tumour is **malignant** or **benign** from cell measurements.

**Workflow followed:** Problem Definition -> Data Collection -> Data Cleaning -> Data Analysis -> Model Development -> Training -> Prediction -> Evaluation -> Conclusion

---

## Project Structure

```
week6_ai_project/
├── Breast_Cancer_Prediction.ipynb   # Main Jupyter Notebook (all 5 tasks)
├── Breast_Cancer_Prediction.html    # Same notebook with outputs, viewable in a browser
├── Final_Project_Report.pdf         # Final project report (10 pages)
├── data/
│   ├── breast_cancer.csv            # Dataset
│   └── results.json                 # Saved model results
├── figures/                         # All charts and screenshots
├── requirements.txt
└── README.md
```

---

## Task 1 - Project Selection and Problem Statement

- **Project:** Breast Cancer Prediction (Disease Prediction)
- **Problem:** Predict whether a tumour is malignant or benign using 30 measurements of the cell nucleus.
- **Why ML:** It is a supervised classification problem with labelled data, and a model can learn patterns from 30 features that are hard for a person to study together.
- **Expected outcome:** A model with more than 95% accuracy.
- **Real-world use:** A second-opinion tool to help doctors with early screening.

## Task 2 - Data Collection and Preprocessing

- **Dataset:** Breast Cancer Wisconsin (Diagnostic), 569 rows and 30 features (from scikit-learn / UCI repository).
- Used Pandas and NumPy to load the data, view `head()` and `tail()`, check shape, data types, missing values and duplicates.
- Result: **0 missing values and 0 duplicates**, so the before and after cleaning numbers are the same. Handling code (median fill and `drop_duplicates`) is still included.
- Target variable: `target` (0 = malignant, 1 = benign).
- Applied `StandardScaler` because the features have different ranges.

## Task 3 - Data Analysis and Visualization

Six visualizations were made, each with a written insight in the notebook:

| # | Chart | Main finding |
|---|-------|--------------|
| 1 | Bar chart - diagnosis count | 357 benign (62.7%), 212 malignant (37.3%) |
| 2 | Histogram - mean radius | Malignant tumours are larger (about 17.5 vs 12.1) |
| 3 | Scatter plot - radius vs area | The two classes are well separated |
| 4 | Box plot - mean concavity | Malignant concavity is over 3 times higher |
| 5 | Correlation heatmap | Radius, perimeter and area are almost the same information |
| 6 | Top 10 features bar chart | Concave points, perimeter and radius matter most |

## Task 4 - Model Development and Training

- X = 30 features, y = target
- Train/test split: **80% / 20%** (455 / 114 records), `stratify=y`, `random_state=42`
- **Model: Logistic Regression** (on scaled data). Chosen because it suits binary classification, the features are almost linearly related to the target, and it is easy to explain.
- Also compared with Decision Tree, KNN and Random Forest.

| Model | Accuracy |
|-------|----------|
| **Logistic Regression** | **98.25%** |
| KNN | 95.61% |
| Random Forest | 95.61% |
| Decision Tree | 91.23% |

## Task 5 - Model Evaluation and Final Report

| Metric | Score |
|--------|-------|
| Accuracy | 98.25% |
| Precision | 0.9861 |
| Recall | 0.9861 |
| F1-score | 0.9861 |
| 5-fold CV accuracy | 98.07% |

**Confusion matrix:** 41 malignant correct, 71 benign correct, 1 malignant predicted as benign, 1 benign predicted as malignant.

The full 10-page report is in `Final_Project_Report.pdf`.

---

## Week 6 Summary

This week I combined everything from the 6-week internship into one complete project: loading and cleaning data with Pandas and NumPy, doing EDA with Matplotlib and Seaborn, building and training a model with Scikit-learn, and evaluating it with proper metrics. I also learned why train/test splitting, feature scaling (fit only on training data) and looking at recall (not only accuracy) are important in a medical problem.

## How to Run

```bash
git clone <your-repo-link>
cd week6_ai_project
pip install -r requirements.txt
jupyter notebook Breast_Cancer_Prediction.ipynb
```

Then click **Kernel -> Restart & Run All**.

## Future Scope

- Hyperparameter tuning with GridSearchCV
- Artificial Neural Network using TensorFlow / Keras
- Bigger dataset from multiple hospitals
- A small Streamlit / Flask web app for predictions

## Tools Used

Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Jupyter Notebook

> Note: This project is for learning purposes only and is not meant for real medical diagnosis.
