Ashley Teraishi Delaney Nikoofekr Sergio Quiroz Jordan Guzman

Stellar-Classifier

Introduction:

For our final project, we worked on a [stellar-classifier dataset](https://www.kaggle.com/fedesoriano/stellar-classification-dataset-sdss17) that was found on Kaggle. The objective is to predict what type of stellar object was being viewed, whether they were Stars, Galaxies, or Quasars.  This project had its difficulties but was also very interesting given we were predicting stellar objects.

Selection of Data:

The data consists of 100,000 observations of space objects taken by the SDSS (Sloan Digital Sky Survey).  Every observation is described by 17 feature columns and 1 class column which identifies it to be either a star, a galaxy, or a quasar.

The features that relate mainly to the scan/camera data rather than the stellar object data that were dropped are the following: ‘cam\_col’, ‘obj\_ID', 'run\_ID', 'rerun\_ID', ‘field\_ID', ‘fiber\_ID', 'spec\_obj\_ID' and 'MJD'.  These features were unnecessary for making our predictions.  We also dropped ‘u’ and ‘z’ because we found ‘g’, ‘r’, and ‘i’ to have higher correlations with the other features.

The data has seven numeric features: ‘alpha’, ‘delta’, ‘g’, ‘r’, ‘i’, ‘redshift’ and ‘plate’. There is one categorical category labeled ‘class’.

The categorical feature was encoded using OneHotEncoder and transformed so the model predictions could be more accurate.

Methods:

Tools:

- Numpy, Pandas, Matplotlob
- Seaborn for analysis and visualization
- Anaconda for Jupyter Notebook and for submission
- Google Colab for keeping one codebase for the team to contribute to

Inference methods used with Scikit:

- Models:  KNeighborsClassifier, DecisionTreeClassifier, SVC, and LogisticRegression
- Preprocessing:  OneHotEnconder, StandardScaler
- Hyperparameter Tuning:  GridSearchCV

Process: (forward selection)

Choice of predictors:  It turns out after plotting multiple graphs and finding correlations amongst the features, 'redshift', 'g', and 'redshift' vs 'g' shows to be very good at classifying, with each class clearly having its own value range.  The redshift value is based on the increase in wavelength and the g value is the green filter in the photometric system.  We concluded that this is the best way to classify stellar objects. Therefore, the strongest predictors in the dataset are 'g' and 'redshift' as seen in the graph below.

![](Aspose.Words.14483e7e-c22e-42e3-8a6f-212e0a7f5934.001.jpeg)KNN: After trying the KNN model we saw that the accuracy would go down as the number of neighbors went up, but with a number too low we were overfitting the data. We set the weight parameter to distance and for the metric parameter we used manhattan.  After training the model, the accuracy came back to be 95%.

LogisticRegression:  This model is a predictive analysis algorithm based on the concept of probability.  After scaling the data and exploring it, we see that liblinear provided the best learning curve.  However, after training the model the accuracy was slightly less than KNN which was 95%.  Logistic regression resulted in an accuracy of 93.4%

DecisionTreeClassifier:  This model splits between nodes which will optimally divide the data into the correct categories.  After running the model, the nodes were divided based on the redshift predictor.  In adjusting the max depth of the decision tree classifier to see the results, we discovered the optimal max depth to be 5.  We chose 5 because anything more than 5 did not affect the accuracy of the model significantly.  The resulting accuracy of the model was 96.5%.

SVC:  This model does not require one-hot encoding, so we were able to use the class column as is for our target.  We scaled the training and test data.  We used the default SVC hyperparameters for this model.  The resulting accuracy of the model was 96.2 %.

Results:

After the study was completed, we found the decision tree classifier was the best model. This was because after the model was trained it had a 96.5% accuracy of classifying stellar objects.  This accuracy also accounted for the misclassifications when training the model.  As seen on the redshift vs g classes chart below, the misclassification appeared to be mostly between 21 to 23 along the y-axis.  However, we would say the results of the project were successful and answered the initial question which was to classify stellar objects.  We also went a step further and tested our model against 732,646 new objects from an [SDSS data set from 2016](https://www.kaggle.com/joshmcadams/sdss-16). With this new data, our model successfully predicted these objects with a 98.3% accuracy.

Misclassifications graph:

![](Aspose.Words.14483e7e-c22e-42e3-8a6f-212e0a7f5934.002.png)

Discussion:

After exploring the data and implementing the various machine learning models, we found that the decision tree classifier gave the best accuracy.  This was done by trying different hyperparameters the model trained with to produce the best result.  KNN and logistic regression was also attempted but did not produce as accurate of a result.  The decision tree model with the default settings for the hyperparameters proved to be the best fit.

The perspective of future research is that there may be an ability to classify more stellar objects in the future such as black holes, different types of stars, and maybe even gravitational pull.

Summary:

This stellar prediction project supervised classification models to predict stellar objects. These predictions are based on 7 features:  ‘alpha’, ‘delta’, ‘g’, ‘r’, ‘i’, ‘redshift’ and ‘plate’. In conclusion, after using several different types of models, the decision tree model was the best with an accuracy of 96.5%.
