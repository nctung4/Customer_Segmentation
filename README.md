# Customer Segmentation

The focus of this project is on cluster analysis, and classification modeling on a customer database.

### Dataset
This dataset was published on kaggle, available [here](https://www.kaggle.com/arjunbhasin2013/ccdata).

### Resources used:
**Python Version:** 3.8.5 <br>
**Packages:** pandas, numpy, sickit-learn, matplotlib, xgboost, seaborn, joblib <br>
**Requirements:** ```pip install -r requirements.txt```  

### Table of Contents:
1. [Overview](#overview)
2. [Project Motivation](#project-motivation)
3. [Technical Aspect](#technical-aspect)
4. [Major Results](#major-results)
5. [Credits](#credits)

### Overview
This notebook's purpose is to develop a customer segmentation model to define a marketing strategy. The sample Dataset summarizes the usage behavior of about 9000 active credit card holders during the last 6 months. The file is at a customer level with 18 behavioral variables. After the segmentation, I created several classification models for the clusters. I tried to analyze the data in respect of the CRISP-DM methodology. The last phase of the CRISP-DM model is the deployment, which is not within the scope of this project, however, I will mention a few ideas on how to deploy this project in production. The analysis can be found [here](https://github.com/nctung4/Customer_Segmentation/blob/main/Analysis.ipynb).

### Project Motivation
Nowadays clustering is crucial for marketers. Clustering will reveal an astonishing level of nuances that allow marketers to identify groups of like-minded people within their customer base. It unlocks profound insights that can’t be seen when looking at customers as a whole.

The deep customer understandings that result from clustering can (and should) inform every task a brand engages in, from product development and merchandising to message development, promotions and targeting. More than that, clustering enables a company to view its business from the lens of its customers, rather than its products. That’s game-changing.

I wanted to broaden my knowledge in this topic, and therefore I decided to search for an existing data table, where I can apply these essential techniques.

### Technical Aspect
This project can divided into 2 parts:

**1. Clustering:**

* I used the k-Means algorithm on the cleaned dataset for creating the clusters.
* I decided the optimal number of clusters with the elbow method and silhouette scores.
* With PCA I checked that how many components do we need, to explain most of the variance of the data.
* Last but not least I concated the cluster results with the cleaned dataset.

**2. Classification:**

* I tried several models, for instance KNN, SVC, Decision Tree, Random Forest, XGBoost, Logistic Regression etc.
* I used grid search for finding the best parameters for each model.
* I plotted the confusion matrix and learning curve, to check the model performance.
* At last, I applied a voting classifier ensemble technique, to have the most accurate result.

### Major Results

One of the most important thing to check firstly, is that how the variables are correlated with each other.

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/Corr_matrix.png)
We can see that most of the variables are not correlated with each other.
It is good for us, because in supervised learning the stronger the correlation, the more difficult it is to change one variable without changing another. It becomes difficult for the model to estimate the relationship between each independent variable and the dependent variable independently because the independent variables tend to change in unison.

After applying PCA on the cleaned dataset, we can see that the number of components required to explain the data is extremely important: we need approximately 10 components to explain 90% of the variance of the data.

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/PCA.png)

**Clustering:**

I applied the elbow method, to determine the optimal number of clusters:

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/Elbow_method.png)

From the elbow method we can see that the optimal number of cluster is around 5.-7. After that, I checked the silhouette score for each cluster, and there were no significance difference at all. Therefore I chose the number 6, because it had the most balanced result.

**Classification:**

The most accurate final models were the Support Vector Classifier, and the Logistic Regression. They both had approximately 98% accuracy, on the dataset.

**Support Vector Classifier:**

Confusion matrix:

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/Confusion_matrix_SVM.png)

Learning Curve plot:

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/Learning_curve_SVC.png)

**Logistic Regression:**

Confusion matrix:

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/cm_lr.png)

Learning Curve plot:

![](https://github.com/nctung4/Customer_Segmentation/blob/main/plots/lc_lr.png)

In the learning curve, we can see from the training score (red line), that both model have low bias, because they had a great accuracy on the training set, and also on the test set. Therefore we can say, that both model have low variance as well. Overall a model with low bias and low variance is an optimal model.

### Credits
I am absolutely grateful to [Hadelin](https://www.linkedin.com/in/hadelin-de-ponteves-hon-phd-1425ba5b/?originalSubdomain=ae) and [Kirill](https://www.linkedin.com/in/keremenko/?originalSubdomain=au) for creating such amazing ML courses on Udemy. In addition, I want to thank [F.Daniel](https://www.kaggle.com/fabiendaniel/customer-segmentation) for creating and explaining his work on his own specific business problem.
