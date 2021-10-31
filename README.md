# Course: Model Based Statistical Learning
# Project Clustering: Expectation Maximization(EM) algorithm - Gaussian Mixture Models(GMM)
In this work, we implement from scratch the EM-algorithm for GMM in R. It is applied to multivariate data, more specifically the wine dataset available in the pgmm package. This dataset contains chemical characteristics about three types of wine. We use AIC, BIC and the likelihood as metrics to identify an adequate number of clusters. To assess the quality of the clustering, we use the function classError and adjustedRandIndex from the Mclust package. We compare the results of GMM with another clustering algorithm (k-means), and against the ground truth, that is the original wine type. Additionally, we explore two types of initialization for the parameters of the model, we refer to them as random centroids initialization and k-means initialization.

#### Author: Mariana Chavez - Franz Franco Gallo


## Useful functions

In this section we define the functions that will help us in our analysis.

* `logsumexp` computes the log of the sum of the exponential of each entry of a vector $x$. This is useful for the computation of the log-likelihood and the responsibilities $ \gamma(z_{nk}) $.
* We create two functions, `initialization.random_centroids` and `initialization.k_means`, for the initialization of the parameters $\mu_k$, $\sigma_k$ and $\pi_k$. Given $K$, the number of clusters, `initialization.random_centroids` randomly samples $K$ points of the data and sets them as the initialization of $\mu_1, \ldots , \mu_k$. The variance-covariance matrix of the data $X$ serves as initialization for each $sigma_k$. Each $\pi_k$ is set to $1/K$. The second function, `initialization.k_means`, runs k-means on the data $X$. Then it uses the final centroids produced by k-means to initialize each $\mu_k$. It computes the variance-covariance matrices of the clusters found by k-means to initialize each $\sigma_k$. Finally, each $pi_k$ is initiliazed according to the number of elements in the clusters.
* Given a dataset $X$ and a number of desired clusters $K$, `EM_algorithm` computes the EM algorithm. One of the previously described initializations must be chosen.     
* `classify` takes the resulting means ($\mu_1, \ldots, \mu_K$), variances ($\sigma_1, \ldots, \sigma_K$), and proportions ($\pi_1, \ldots, \pi_K$) of the EM algorithm and classifies the points in $K$ clusters.
* `metrics` computes the likelihood, AIC and BIC. 
* `crossvalidation.EM` performs cross-validation on the EM-algorithm. It evaluates the log-likelihood.   
* Subsequently we present several functions related to plotting. 

## Data loading
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/data_loading.png" width="1000"><br>


## The EM algorithm
### Clustering comparison results
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/clustering_comparison.png" width="1000"><br>
### Mean convergence
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/mean_convergence.png" width="1000"><br>
### Log-likelihood convergence
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/loglik_convergence.png" width="1000"><br>

## EM algorithm vs k-means
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/EM_vs_Kmeans.png" width="1000"><br>
## Number of clusters selection
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/EM_vs_Kmeans.png" width="1000"><br>
## Towards higher dimensions
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/EM_vs_Kmeans.png" width="1000"><br>
## Conclusion
* We explored two possible initializations for the parameters of the EM-algorithm. The random centroids initialization outperformed the k-means initialization in our experiments. 
* The convergence of the means is smother and faster using k-means initialization. Nevertheless, random centroids initialization produces better values of log-likelihood, AIC and BIC. 
* Using $K=3$ and random centroids initialization is the option that better emulates the ground truth.  
* AIC, BIC and the cross-validation log-likelihood were used to select the number of clusters. In the bivariate scenario BIC and the log-likelihood suggest extracting 2 clusters, while in higher dimensions they suggest 2. 
