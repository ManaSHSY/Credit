# Credit
This code is intended to provide a simple solution to a Kaggle Data Science Challenge, known as GiveMeSomeCredit 
 Author: Mana Shahriari Date created: 2021/11/28 
 Description: Demonstration of Dataset:GiveMeSomeCredit https://www.kaggle.com/c/GiveMeSomeCredit/data

General Approach
At the beginning a data exploration of the training dataset is performed i.e. the head of data frame, size of training dataset, general information, and description. One column of data frame is removed (Unnamed: 0). This column does not appear in DataDictionary, so is not part of data and seems to be only a counter. After this extra column is removed, 11 column from this data frame is remained. 
The Target Class i.e. SeriousDlqin2yrs is plotted (a bar chart) to provide some info on this classes. The bar chart show imbalanced classes for this dataset. Additionally, observing the correlations shows the highest correlation of target class with NumberOfTime30-59DaysPastDueNotWorse. 
Then it comes to the remaining 10 columns of this data frame. After exploring them, it is noticed that we have missing data in two columns. The column MonthlyIncome has around 20% of its data missing, whereas the missing data in NumberOfDependents is around 2% of the this column. We can ignore the 2% and simply remove NaN from this column, but for MonthlyIncome we take a strategy to fill missing numbers. The highest correlation of MonthlyIncome is with NumberRealEstateLoansOrLines. With the help of groupby, we use the mean of this column to deal with the missing data in MonthlyIncome column. 

After little bit of data exploration, data cleaning and visualisation, and dealing with missing data, we can preprocess the data; i.e. normalize it to have zero mean and a standard deviation equal to one.  
The training data is then split into four groups; features vectors and label vector for training set and validation set. X or the feature vector is of size 10, and the label y is binary. Validation set is chosen to be 20% of the whole training dataset and to avoid data leakage normalization of features are done on training features. 
A deep learning model is chosen to build the model due to the dimension of training samples. Because of imbalanced classes, the model is trained with class weight. The negative class is almost 12 times the positive class, so the weight is chosen accordingly. 
Finally AUC is used to access the performance of validation set. 

To evaluate the model on test dataset, we can simply feed test data into the model.

Some of the hyperparameters of the model can be chosen using Keras Tuner. The process of selecting the right set of hyperparameters for is called hyperparameter tuning or hypertuning. Here, the model is defined first and then the tuner is instantiated and hypertuning is performed. The tuner later searches for the best parameters and report the best results. The model can be trained with the optimum hyperparameters.


