# MPM_Rajasthan
Mineral prospectivity mapping (MPM) of base metal and gold ore deposits in souther Rajasthan, India
This repository is a collection of source code, model building workflow and relevant documentation for MPM with machine learning and Deep learning algorithms.

---

## 🚀 MPM building and validation

We have used R-based script for reading various raster files and have been resampled to match reference raster file resolution. All the raster files were stacked to generate a multilayer single raster stack file. The stacked raster file was saved as Geotif file. This Geotif file will be used as input data of the below given random forest model building and MPM generation.

User should run the codes as per the given information:
1. MPM_RF_with_uncertainty.ipynb - Model training and validation
2. MPM_RF_prospect_area.ipynb - Estimate of most highly prospective area
 
Here are the steps in brief for the MPM and most probable MPM (with low uncertainty) using python-based programming workflow:
- Libraries and Setup for working directory
- Preparing data for stacking and generating Geotif file
- Data processing and stacked data layer creation
CSV file (“Multiclass_Mineral_data.csv”) contains labelled data loaded for training.
Datasets cleaned (for missing values) and converted for multiclass classification of target variables (COMMODITIES’).

### Model Training
RF, SVM, 1D-CNN and SVM classifier for multiclass classification.
k-fold (3-fold) cross validation implemented to train and validate model performance.
All relevant metrices have been calculated.

### Model Evaluation
Training model evaluated using variable importance for understanding feature significance, analyzing predictive performance from ROC curve and AUC scores for each class.

### Spatial prediction
2D MPM model probabilistically predicts across the study area by training RF, SVM, CNN and ANN.
Each predicted model saved as Geotif file (‘Class_Random_Forest_Prediction.tif’)
ROC curve generation and display for each class.

### Uncertainty Estimation
Based on spatial predictions, uncertainty quantification was done for RF model only using “Bootstrap method”.

### Visualization 
Generation and display of ROC for each class.

### Prospect area quantification

Quantification of probable mineral prospective area was created using low uncertainty and high probability MPM generated from RF through Python-based programming language and output as Geotif file.

