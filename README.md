# CryptoClustering
I worked with ChatGPT 4o to complete this module assignment.

<div align='center'>
    <img src='https://images.pexels.com/photos/577585/pexels-photo-577585.jpeg' height='300' title='ML Mysticism' alt='African American Women trying to comprehend Machine Learning'/>
</div>

## Overview
* Clustering Explained: The process of clustering data points into groups is called centering, which helps determine the number groups to create. K-means algorithm is the simplest and most common algorithm used to group data points into a cluster.
* Utilize K-means algorithm and Principal Component Analysis(PCA) to classify/cluster cryptocurriencies according to their price fluctuations across the following timesframes: 24 hours, 7days, 30 days, 60 days, 200 days, and 1 year.


## Methods
* ### Elbow Method & Inertia
    * Elbow Method is used to determine the optimal value of k, or the number of clusters in a dataset by running the K-mean algorithm for range of possibilities for k, and the resulting elbow curve plots the number of cluster of x, versus an objective function called inertia.
    * Inertia is commonly used as an objective function representing the sum of the squared distances of samples to their closest cluster center. The goal is to find the spot on the chart where the value for k that corresponds to a measure of inertia that shows minimal change for each additional cluster that is added to the dataset. The spot is indicatd by the bend in the elbow.

* ### Preprocessing & PCA
    * Preprocessing - In order to determine the optimal k-value, data must be encoded (replace strings and texts with numbers) and scaled/standardized before ML models can be fitted to the data.
    * PCA - statistical technique used to reduce the number factors or noise by transforming dataset with a large set of features into a smaller one that contains MOST of the information from original dataset. 

## Landscape
* Maching Learning (ML) is the practice of applying computer algorithms and statistics to create models models that can learn from past data and then make decisions or predictions about future data. Here are several types of ML: 
    * Regression
    * Clustering
    * Neural Networks
    * Deep Learning

* ML models can be grouped into 2 main buckets: 
    * Unsupervised Learning: algorithm makes sense of unlabeled dataset by extracting features and patterns on its own. 
    * Supervised Learning: algorithm learns on labeled dataset where each example in the dataset is tagged with the answer. This provides an answer key that can be used to evaluate the accuracy of the model.

## Business Advantage
* ML allows for decisions to be made more quickly and efficiently, streamlining operational processes across many industries, and improving responsiveness to customer demands.

* Clustering - unsupervised learning can be used to categorize relationships among data points for the purpose of identifying clusters or related groups and trends to target with some kind of the action such a product offerings or marketing campaigns. Here's a list:
    * Customer Segmentation
    * Recommendation Systems
    * Targeted Marketing

## Results
*   ### Scaled data, Found best k-value, & Clustered Data
    * Utilized `StandstardScaler()` module from `scikit-learn` to normalize and scale the data first.
    * Created `for` loop to determine the optimal k-value based on a range from 1 - 11. Used the Elbow method plot the inertia and k-values to determine the optimal k-value.
    * Clustered with K-Means based on the optimal k-value of Scaled DF

<div align='center'>
    <img src='https://raw.githubusercontent.com/N8sGit/ai_project_group_8/4398f2237ab162ddcca84e87e857f19a2769ef71/exported_plots/companies.png' height='300' title='Scaled DF Clusters' alt='Scaled DF Clusters'/>
    <p>Scaled DF Clusters</p>
</div>

*   ### Performed PCA & Found best k-value, & Clustered Data
    * Reduced DataFrame to 3 principal components, determined how much information was attributable to each component through explained variance, determined total explained variance.
    * Created `for` loop to determine the optimal k-value based on a range from 1 - 11. Used the Elbow method plot the inertia and k-values to determine the optimal k-value.
    * Clustered with K-Means based on the optimal k-value of Scaled DF reduced to 3 principal components.

<div align='center'>
    <img src='https://raw.githubusercontent.com/N8sGit/ai_project_group_8/4398f2237ab162ddcca84e87e857f19a2769ef71/exported_plots/companies.png' height='300' title='PCA Clusters' alt='PCA Clusters'/>
    <p>PCA Clusters</p>

*   ### Determined the Weight of Each Feature on Each Principal Component
    * Utilized the attribute `pca.components_` as well the `.T` property of NumPy arrays in pandas to transpose each feature into a row, and each component into a column in order. `pca.components_` is an attribute that stores the principal components and the vector of weights, which represent the contribution of a each feature to the different components.
    *   The goal of PCA is to find the axes (principal components) that maximize the variance of the data points, or in other words the direction in each features space that captures the maximum variance in the data. Hence high positive vector weights implies the feature has a strong influence on principal components in the positive direcction. A high negative vector weight implies the feature has a strong influence on the principal component in the negative direction.
  
        * Regarding PCA1, the **"price_change_percentage_200d"** had the strongest positive influence with .594468 and **"price_change_percentage_24h"** had the strongest negative influence with -0.416728.

        * Regarding PCA2, the **"price_change_percentage_30d"** had the strongest positive influence with .562182 and **"price_change_percentage_1y"** had the only negative influence with -0.150789.

        * Regarding PCA3, the **"price_change_percentage_7d"** had the strongest positive influence with 0.787670 and **"price_change_percentage_60d"** had the strongest negative influence with -0.361377.  

## Recommendations

* ### Clarify the Difference b/t Explained Variance vs Explained Variance Ratio
    * Explained Variance - quantifies the amount of total variance in the data captured by principal component
    * Explained Variance Ratio - proportion of the total variance in data capture by each principal component.

