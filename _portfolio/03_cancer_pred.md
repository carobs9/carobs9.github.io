---
title: "Breast Cancer Prediction"
excerpt: "Small cancer prediction project."
collection: portfolio
permalink: /projects/breast-cancer-pred/
tags:
	- machine-learning
	- deep-learning
	- healthcare
	- python
---
> This project aims to classify tumors into benign or malignant based on several numerical features stored in the Wisconsin Breast Cancer dataset.

## Project at a Glance

Using the classic Wisconsin Breast Cancer dataset, I built a machine learning workflow that predicts whether a tumor is likely to be benign or malignant. The project contains an exploratory analysis and feature selection, as well as model comparisons.

## Dataset

- **Source:** Wisconsin Breast Cancer Diagnostic dataset (via `sklearn.datasets`)
- **Samples:** 569 patient records
- **Features:** 30 numerical descriptors extracted from digitized images of cell nuclei (e.g., radius, texture, perimeter, area, smoothness, concavity)
- **Target:** Binary label indicating benign vs. malignant

Working with this dataset is a great playground for handling class imbalance, multicollinearity, and feature scaling in a medically relevant setting.

## Approach

1. **Data preparation**  
	- Loaded the dataset from scikit‑learn and organized it into feature/target data frames.  
	- Checked for missing values and inspected the class distribution.  
	- Applied Min‑Max scaling to put all features on a comparable range.

2. **Exploratory data analysis (EDA)**  
	- Generated statistical summaries for both classes (benign vs. malignant).  
	- Visualized feature distributions and relationships using kernel density plots, pair plots, and correlation heatmaps.  
	- Identified highly correlated features and patterns that could simplify the model while preserving signal.

3. **Feature selection pipeline**  
	I implemented several complementary strategies to understand which features actually matter:
	- Correlation‑based pruning to remove strongly collinear variables.  
	- Univariate tests (e.g., chi‑squared) to select top‑scoring features.  
	- Recursive feature elimination (RFE and RFECV) with a tree‑based model.  
	- Principal Component Analysis (PCA) to study lower‑dimensional representations and explained variance.

## Neural Network Model

The final classifier is a custom feed‑forward neural network implemented in Keras:

- Input layer covering the selected features (30 to start, reduced after selection).  
- Several dense layers with ReLU activations.  
- L2 regularization and dropout to reduce overfitting.  
- Sigmoid output neuron for binary classification.  
- Trained with Adam optimizer and binary cross‑entropy loss.

I also trained a traditional Random Forest model as a baseline to benchmark the deep learning approach.

## Results

- Training accuracy converged to around the high‑90% range.  
- Validation performance stayed close to training accuracy, suggesting decent generalization.  
- Confusion‑matrix analysis showed a high true‑positive rate and relatively few false negatives (critical in this type of task), along with strong performance on benign cases.

In short, the deep learning model consistently outperformed the Random Forest baseline on this dataset.

## Tools and Skills

- **Languages:** Python  
- **Data & ML:** NumPy, pandas, scikit‑learn, Keras  
- **Visualization:** Matplotlib, Seaborn  
- **Concepts:** feature engineering, feature selection, regularization, cross‑validation, neural networks, model comparison, evaluation metrics.

## What I Focused On

- Building a clean, readable workflow inside notebooks, from EDA through to modeling.  
- Experimenting with different feature subsets and architectures to see how they affect performance.  
- Practicing good habits like scaling, baseline models, and careful evaluation instead of chasing a single accuracy number.

## Explore the Code

You can dive into the notebooks, experiments, and documentation here:

- GitHub repository: [carobs9/breast-cancer-pred](https://github.com/carobs9/breast-cancer-pred)

Feel free to browse the notebooks for detailed plots, intermediate experiments, and more commentary on each step of the pipeline.

