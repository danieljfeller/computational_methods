**Feedforward networks** provide a universal system for representing functions because __for every function there exists a feedforward network that approximates this function__. This is achieved by learning _representations_ of the data. Deep learning relies on the assumption that _the function we want to learn involves composition of several simpler functions._ There are 2 main motivations behind using deep learning models:

1. We want to learn a representation of the data that is composed of simpler representations (eg. corners defined in terms of edges or n-grams in a document).
2. Learning a sequence of sequentially dependent steps (eg. first locate a set of objects, then segment them from each other, then recognize them)

 In other words, the learning problem consists of discovering a set of underlying factors of variation that can in turn be described in terms of other, _simpler_ underlying factors of variation. Empirically, **greater depth of networks does seem to result in better statistical generalization.**

## How do deep learning models learn?

The fundamental procedure for learning model parameters in deep learning is achieve through **gradient descent** and **backpropigation**. First, we build a computational graph for each vector that tracks the operations that were performed on that vector. Second, we then use the computational graph to compute the partial derivative of the loss function with respect to each model weight. These partial derivatives give us the **gradient of the loss function**. We then **update the model weights using gradient descent**. In short, the gradient descent algorithm attempts to find a local minimum of the loss function by iteratively updating the weights of the model using the gradient computed using backpropigation. Gradient descent uses a simple update rule that subtracts the gradient (multiplied by the learning rate) from the model parameters.


#### Training Procedure
1. Define a neural network that has parameters that we will learn (aka weights)
2. Iterate over a dataset of inputs (aka 1 epoch)
3. Process every input through the network (**forward propigation**)
4. Compute the loss (using the preselected objective function)
5. Propagate gradients back into the network’s parameters (aka **backpropigation**)
		- this is accomplished by tracking all computations performed on the learnable parameters

![Backpropigation](https://cdn-images-1.medium.com/max/1600/1*q1M7LGiDTirwU-4LcFq7_Q.png)


### What about model architecture?

Fully connected layers are the building blocks of many networks but some models have layers where not every node in one layer is connected to all nodes in the subsequent layer. Many architectures feature **skip connections** that reduce the number of connections, thereby making it easier for the gradient to flow from output layers to layers closer to the input. Many specialized networks such as *RNNs* and *CNNs* have fewer connections so that each unit in the input layer is connected to only a small subset of units in the output layer, __although these are most useful for specialized problems__ (eg. computer vision or NLP).

Each node in a neural network has an **activation function**. In modern neural networks, the default recommendation is to use _rectified linear units_. Because RELU is nearly linear, they preserve some properties that make linear models easy to optimize with gradient-based methods while making it easier for the linear model to minimize testing error. This is why __RELU units are the most common choice for hidden units__. As shown below, there are additional types of activation functions possible. In the past **logistic sigmoid** and **hyperbolic tangent** units were population, but they can make gradient-based learning very difficult and thus their use in feedforward networks is now discouraged (although some RNNs leverage sigmoid units).

Of course, no model is complete without an _output_, and there are several common choices for neural network units as outputs. **Linear units** are the simplest type of unit and give a continuous vector as an output. Because linear units do not _saturate_, they pose little difficulty for gradient-based optimization algorithms. **Sigmoid units** are used for binary classification problems. Unlike using linear units with binary outputs, sigmoid units ensure that there is always a strong gradient whenever the model has the wrong answer. **Softmax units** are used for multi-label classification problems because they represent the probability distribution over _n_ different classes (and the probabilities of those _n_ classes always sum to 1).

_Note that any kind of neural network unit that may be used as an output can also be used as a hidden unit._

![Activation Functions](https://cdn-images-1.medium.com/max/1200/1*ZafDv3VUm60Eh10OeJu1vw.png)

### What about initialization?

For feedforward neural networks, it is important to initialize all weights to small random values. Stochastic gradient descent applied to non-convex loss functions has no convergence guarantee and is sensitive to the values of the initial parameters.
