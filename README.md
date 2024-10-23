# Forest-cover-classification
## 1. Introduction
The project focuses on classifying forest cover types using cartographic variables like elevation, slope, and soil type. The dataset, derived from the U.S. Forest Service, contains 30-meter square patches of land, and each patch is labeled with one of seven forest cover types. The goal is to build a machine learning model that can predict the cover type based on the available features, aiding in environmental management and forestry practices.

For more information, you can visit the [Kaggle competition page](https://www.kaggle.com/competitions/clasif-cubiertas-forestales).

## 2. Technology Used
The project was developed using Python as the primary programming language. Key libraries such as Scikit-learn, Pandas, and NumPy were utilized to perform tasks related to machine learning, data manipulation, and numerical computations. These libraries provided the essential tools for building the classifier, preprocessing data, and optimizing the model's performance.

## 3. Code Development

### 3.1 Data Preprocessing
The methodology used for data preprocessing involved removing samples considered as outliers to reduce noise when training the classifier. Isolation Forest algorithm from Scikit-learn library was employed to identify these outliers.

Regarding the imbalance of samples across classes in the training dataset, no preprocessing was applied since the chosen algorithm, XGBoost, handles this internally.

### 3.2 Algorithm Selection
An XGBoost classifier was trained using the training dataset to obtain the probability of each test sample belonging to each class. Weighted scores were then calculated by multiplying these probabilities by the cost matrix, allowing the final class of each sample to be determined based on the lowest weighted score. This approach optimizes costs of classification errors according to the penalties defined by the cost matrix.

### 3.3 Hyperparameter Selection
For hyperparameter optimization, GridSearchCV algorithm from Scikit-learn library was used. This method performed a parametric sweep with different values for each hyperparameter to find the best estimation.

A cross-validation value of 3 was used, which divides the training dataset into three equal parts and uses one as the test set in each iteration.

In our specific case, the classifier's optimized parameters were: `n_estimators`, `learning_rate`, `max_depth`, and `subsample`.

## 4. Results
The developed solution achieved first place in the Kaggle competition by making predictions with the lowest average cost associated with classification errors. This performance was based on minimizing the penalties defined in cost matrix, demonstrating the effectiveness of the model and its ability to optimize for real-world costs of misclassifications.
