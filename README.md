# Anemia Detection & Hemoglobin Estimation with AI

### Comparative Study of Machine Learning and Deep Learning Models

Author: Eduardo Gonzalo Bautista Arrilucea
Focus: Data Science | Machine Learning | Computer Vision | Model Evaluation

## Overview

This project compares traditional Machine Learning and Deep Learning approaches for anemia detection and hemoglobin estimation using image analysis.

Two predictive tasks are investigated:

1. Binary classification: identifying images labeled as anemic or non-anemic.
2. Regression: estimating hemoglobin concentration (Hb) using eye images and associated metadata.

The project implements an end-to-end experimentation workflow covering data preprocessing, feature engineering, model training, hyperparameter optimization, model comparison, and performance evaluation.

This is a research and portfolio project, not a medically validated diagnostic system.

## Key Results

| Task | Best Model | Metric | Result |
|---|---|---|---|
| Classification | kNN + SMOTE | ROC-AUC | 0.9182 |
| Classification | kNN + SMOTE | Accuracy | 81.31% |
| Classification | kNN + SMOTE | F1-score | 0.8507 |
| Regression | DeiT / Vision Transformer | MAE | 1.6647 g/dL |
| Regression | DeiT / Vision Transformer | RMSE | 2.1697 g/dL |
| Regression | DeiT / Vision Transformer | R² | 0.2636 |

These results were obtained from the experimental test partitions recorded in the notebook and should not be interpreted as clinically validated performance.

## Datasets

### CP-AnemiC

A dataset containing 710 labeled images:

- 424 anemic images
- 286 non-anemic images

This dataset was used for binary classification experiments.

### EYESDEFYANEMIA

A dataset containing eye images with hemoglobin measurements and associated demographic information.

After image validation and removal of unreadable files, 154 observations remained for regression experiments.

The datasets are referenced through Kaggle input paths and are not distributed within this repository.

## Methodology

### 1. Data Preprocessing and Feature Engineering

The workflow includes:

- Image loading and resizing
- Color normalization and white balance
- Contrast enhancement using CLAHE
- Feature extraction from RGB, HSV, and LAB color spaces
- Statistical feature generation
- Construction of numerical feature matrices
- Training, validation, and testing splits
- Feature scaling and normalization
- Class balancing with SMOTE
- Hyperparameter optimization

The classification workflow produces 117 image-derived features per observation.

The classical regression workflow uses 120 features combining image-derived information and metadata.

### 2. Machine Learning Classification Models

The following models were implemented and evaluated:

- k-Nearest Neighbors (kNN) with SMOTE
- RUSBoost
- Convolutional Neural Network (CNN)
- MobileNetV2 with Support Vector Machine (SVM)
- DeiT / Vision Transformer

#### Classification Results

| Model | ROC-AUC | Accuracy | F1-score |
|---|---|---|---|
| kNN + SMOTE | 0.9182 | 0.8131 | 0.8507 |
| MobileNetV2 + SVM | 0.8692 | 0.7383 | 0.7910 |
| DeiT / Vision Transformer | 0.8656 | 0.7290 | 0.7820 |
| RUSBoost | 0.5823 | 0.5981 | 0.7485 |
| CNN | 0.5080 | 0.5981 | 0.7485 |

The kNN + SMOTE model achieved the highest recorded ROC-AUC score.

Classification performance was analyzed using accuracy, precision, recall, specificity, F1-score, ROC-AUC, and confusion matrices.

The experiments also highlight the importance of examining class-specific errors rather than relying exclusively on accuracy or F1-score.

### 3. Hemoglobin Regression Models

The project also compares regression algorithms for estimating hemoglobin concentration.

Implemented approaches include:

- Ridge Regression
- Support Vector Regression (SVR)
- MobileNetV2 with demographic features
- SLIC with Graph Attention Network
- DeiT / Vision Transformer

#### Regression Results

| Model | MAE (g/dL) | RMSE (g/dL) | R² |
|---|---|---|---|
| DeiT / Vision Transformer | 1.6647 | 2.1697 | 0.2636 |
| Support Vector Regression | 1.7450 | 2.2534 | 0.2057 |
| Ridge Regression | 2.2702 | 3.1093 | -0.5123 |
| MobileNetV2 + age/sex | 2.5379 | 3.3714 | -0.7780 |
| SLIC + Graph Attention Network | 2.6053 | 3.0799 | -0.4839 |

The DeiT / Vision Transformer model achieved the lowest recorded MAE.

However, the R² of 0.2636 indicates considerable unexplained variance, highlighting opportunities for further experimentation and improvement.

## Technologies Used

### Programming and Data Analysis

- Python
- Pandas
- NumPy
- Matplotlib

### Machine Learning

- scikit-learn
- imbalanced-learn
- k-Nearest Neighbors
- Support Vector Machines
- Ridge Regression
- GridSearchCV
- Machine Learning Pipelines
- SMOTE

### Deep Learning

- TensorFlow
- Keras
- PyTorch
- Convolutional Neural Networks
- MobileNetV2
- Vision Transformers
- Graph Attention Networks

### Computer Vision

- OpenCV
- Pillow
- scikit-image
- Image preprocessing
- Feature extraction

### Development Environment

- Jupyter Notebook
- Kaggle Notebooks

## Repository Structure

```text
DETECTION_OF_ANEMIA_WITH_AI/
├── Comparison_AI_Models.ipynb
├── README.md
└── .gitattributes
```

The notebook contains the data preparation workflows, model implementations, experimental evaluations, and saved results.

## How to Run

1. Open Comparison_AI_Models.ipynb in Kaggle Notebooks or a compatible Jupyter environment.
2. Attach the CP-AnemiC and EYESDEFYANEMIA datasets.
3. Configure the corresponding dataset input paths.
4. Install any missing Python dependencies.
5. Execute the notebook cells in sequence.
6. Review the generated model evaluation tables, plots, and performance metrics.

GPU acceleration is recommended for the Deep Learning experiments.

The notebook was developed using Kaggle-specific dataset paths. Dependency versions, hardware, and random seeds may affect reproducibility.

## Key Learnings

This project strengthened practical experience in:

- Developing Machine Learning workflows from data preparation to evaluation.
- Working with classification and regression problems.
- Handling imbalanced datasets using resampling techniques.
- Implementing feature engineering and numerical transformations.
- Comparing traditional Machine Learning algorithms with Deep Learning architectures.
- Selecting evaluation metrics appropriate to different prediction tasks.
- Interpreting model performance and identifying limitations.
- Documenting experimental results and reproducible analytical workflows.

## Limitations

- The available datasets are relatively small.
- The regression experiments have limited sample sizes.
- Model generalization has not been validated using independent clinical populations.
- Differences in image quality and acquisition conditions may influence predictions.
- The reported results do not establish clinical reliability.

The models are intended exclusively for academic research, experimentation, and technical portfolio demonstration.

They should not be used for medical diagnosis or treatment decisions.

## Future Improvements

- Expand and validate the datasets.
- Improve preprocessing and feature engineering.
- Evaluate additional Machine Learning and Deep Learning architectures.
- Apply external validation and more robust cross-validation strategies.
- Investigate model explainability and prediction calibration.
- Improve regression performance and assess generalization.
- Modularize the code into reusable training and evaluation pipelines.
- Add automated tests and dependency management.

## Author

Eduardo Gonzalo Bautista Arrilucea

Bachelor's Degree in Software Engineering
Universidad San Ignacio de Loyola (USIL)

Areas of Interest:
Data Science | Machine Learning | Data Engineering | Artificial Intelligence

GitHub:
https://github.com/EduJhoncito

LinkedIn:
https://www.linkedin.com/in/eduardo-gonzalo-bautista-arrilucea-8a3207261/

---

Academic and portfolio project focused on Machine Learning experimentation, model comparison, and predictive analytics.
