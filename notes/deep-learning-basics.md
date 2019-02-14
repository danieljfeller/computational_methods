The magic of deep learning is that models can learn a _representation_ of the data. This increases model capacity so it can fit the training set and is achieved through stacking **hidden layers** on top of each other.

**How do deep learning models learn?**
The fundamental procedure for learning model parameters in deep learning is through **backpropigation**. First, we build a computational graph for each vector that tracks the operations that were performed on that vector. Second, we then use the computational graph to compute the partial derivative of the loss function with respect to each model weight. These partial derivatives give us the **gradient of the loss function**. We then **update the model weights using gradient descent**. In short, the gradient descent algorithm attempts to find a local minimum of the loss function by iteratively updating the weights of the model using the gradient computed using backpropigation. Gradient descent uses a simple update rule that subtracts the gradient (multiplied by the learning rate) from the model parameters.

**Training Procedure**
1. Define a neural network that has parameters that we will learn (aka weights)
2. Iterate over a dataset of inputs (aka 1 epoch)
	2a. Process every input through the network
	2b. Compute the loss (using the preselected objective function)
	2c. Propagate gradients back into the network’s parameters (aka backpropigation)
		- this is accomplished by tracking all computations performed on the learnable parameters

**What about model architecture?**
Each node in a neural network has a **activation function**. In modern neural networks, the default recommendation is to use _rectified linear units_.

![Activation Functions](https://cdn-images-1.medium.com/max/1200/1*ZafDv3VUm60Eh10OeJu1vw.png)
