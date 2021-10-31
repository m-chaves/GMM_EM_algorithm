# Course: Model Based Statistical Learning
# Project Clustering: Expectation Maximization(EM) algorithm - Gaussian Mixture Models(GMM)
In this work, we implement from scratch the EM-algorithm for GMM in R. It is applied to multivariate data, more specifically the wine dataset available in the pgmm package. This dataset contains chemical characteristics about three types of wine. We use AIC, BIC and the likelihood as metrics to identify an adequate number of clusters. To assess the quality of the clustering, we use the function classError and adjustedRandIndex from the Mclust package. We compare the results of GMM with another clustering algorithm (k-means), and against the ground truth, that is the original wine type. Additionally, we explore two types of initialization for the parameters of the model, we refer to them as random centroids initialization and k-means initialization.

#### Authors: Mariana Chaves - Franz Franco Gallo

To see the complete work download the [EM_algorithm.html file](https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm.html), to see the code check the [EM_algorithm.Rmd file](https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm.Rmd).

Let us show you a glace of the sections and figures:  

## Useful functions

In this section we define the functions that will help us in our analysis.

## Data loading
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/cluster%20data-1.png" width="700"><br>

## The EM algorithm
### Clustering comparison results
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/ellipses%20cluster%202var-1.png" width="1000"><br>
### Mean convergence
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/mu%20plots-1.png" width="1000"><br>
### Log-likelihood convergence
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/loglik%20plots-1.png" width="1000"><br>

## EM algorithm vs k-means
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/comparison%20with%20k-means-1.png" width="1000"><br>
## Number of clusters selection
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/number%20of%20cluster%20selection%20for%20bivariate%20case-1.png" width="1000"><br>
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/EM_algorithm_files/figure-html/EM%20for%207%20clusters-1.png" width="800"><br>
## Towards higher dimensions
<img src="https://github.com/m-chaves/GMM_EM_algorithm/blob/main/images/towards_HD.png" width="1000"><br>
## Conclusion
* We explored two possible initializations for the parameters of the EM-algorithm. The random centroids initialization outperformed the k-means initialization in our experiments.
* The convergence of the means is smother and faster using k-means initialization. Nevertheless, random centroids initialization produces better values of log-likelihood, AIC and BIC. 
* Using $K=3$ and random centroids initialization is the option that better emulates the ground truth.  
* AIC, BIC and the cross-validation log-likelihood were used to select the number of clusters. In the bivariate scenario BIC and the log-likelihood suggest extracting 2 clusters, while in higher dimensions they suggest 2. 
