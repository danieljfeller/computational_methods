Loading Data into Deep Learning Models (using Pytorch)
=======================================================

We now now about the different types of training algorithms for deep neural networks; stochastic gradient descent, mini-batch gradient descent, and batch gradient descent. These methods performed forward-propagation with 1 data instance, a subset of the dataset, and the entire dataset, respectively. As a result, loading data becomes non-trivial and thus it is helpful to have functions that accomplish this for us (rather than defining some arbitrary for-loop every time we train a network).

Pytorchs' `torch.utils.data.Dataset` class is the library's way of representing a dataset. This class **represents a dataset as a dictionary**. In addition, the class takes an optional argument `transform` that performs any required processing on each sample. 
