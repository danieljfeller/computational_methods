**Model Capacity** - abstract idea; refers to the size of the set of possible functions (aka hypothesis space)

**Underftting/Overfitting** - important to ensure both 1) small training error and 2) small gap between the training and testing error
VC dimension - not used in practice

**Regularization** - modifications to a learning algorithm that intend to reduce the generalization error (aka test error) without increasing the training error
	- this can be MORE USEFUL than limiting the capacity of the hypothesis space
	- the algorithm is modified to prefer certain solutions to others; this is sensitive to the size of the dataset (size of the regularization effect becomes smaller as the dataset grows)
	- we add a regularizer to our performance function
	Norm-Based Regularization: we want to minimize the training error (eg. mean-squared error), but we add a penalty such as L2 penalty, ridge pentalty, or weight decay
		- lambda controls the preference of the penalty or the original parameters

**Hyperparameters** - these parameters define the model but are not learned by the algorithm; hyperparameters often control model complexity
	- WE CANNOT USE THE TESTING SET TO FIND THE OPTIMAL HYPERPARAMETERS
	- instead, we leverage a validation set to evaluate several models with different capacities (ie. different hyperparameters); this process is called model selection
	* cross-validation can be used for model selection;

**Maximum Likelihood Estimators:** the hypothesis space is enumerated by theta (our parameter); estimating the likelihood of observing the data with the parameter being tested

In the Bayesian view, estimators express a degree of belief after observing some data and are generally distributions or densities…
	- in bayesian prediction, we are making predictions with the full posterior distribution (not a point estimate)
	- in practice, the maximum apriori probability estimate is used to update parameters

**Suggestions from Nick**
	1.	With a small sample, use permutation analysis and bootstrapping
	2.	Put a bunch of classifiers in a dictionary and write a function or a class to iterate through them all
	3.	Use the net reclassification index for comparing two models

**Pentuum Inc. talk**
1. Image and Report Generation
	- traditional labeling approaches consider targets (diseases) as independent
	- proposal to choose a subset of labels that is likely given the image
	- will use a conditional kernel to simultaneously capture disease-disease correlation and disease-image relevance

2. Similar-patient retrieval
	- distance-metric learning: linear projection matrix to map patients into a feature space
	-
