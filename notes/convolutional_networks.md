A **convolution** is a mathematical operation that averages several measurements to reduce noise and/or dimensionality.

### Motivation for CNNs
Convolution uses 2 important ideas that reduce the memory requirements and improve the statistical efficiency of neural networks:

1. **Sparse Interactions**: Traditional neural networks use matrix multiplication to describe the interaction between each input unit and each output unit and thus have thousands or millions of parameters. In contrast, CNNs have _sparse interactions_ that is accomplished by making kernels smaller than their inputs. For example, for image processing, a model much reduce millions of pixels to a number of small, meaningful features such as edges through the use of kernels. __This property reduces the memory requirements of a model and improves statistical efficiency.__

In the figure below, we can see that the use of kernels (in this example, having a *width of 3*) ensure that fewer output units are affected by the unit. The output units that are affected by a convoluted input are known as **receptive fields**.

![Sparse Connectivity](https://slideplayer.com/slide/13751965/85/images/8/Sparse+connections+due+to+small+convolution+kernel.jpg)

2. **Parameter Sharing**: In a traditional neural network, each element of the weight matrix is used exactly once when computing the output of a layer. In contrast, each value within a kernel is used at every position of the input (except boundary pixels). __The parameter sharing used by the convolution operation means that rather than learning a separate set of parameters for every location, we only learn one set.__ This further reduces the storage requirements for a model.

### Kernels

When performing supervised training with gradient descent, every gradient step requires a complete run fo forward propagation and backward propagation. Obviously, training a CNN in this way is computationally expensive; as a result kernel parameters can also be trained in an unsupervised fashion.

There are 3 basic strategies for obtaining kernels without supervised training:
1. *Random initialization* works surprisingly well and can be used to choose the best CNN architecture. 
2. *Design by hand*
3. *Unsupervised criterion*


### Pooling
In the first stage of a CNN, several **convolutions** are performed in parallel to produce a set of linear activations. In the second stage (aka **detector** stage), each linear activation is run through a nonlinear activation function, such as ReLU. In the third stage, we use a **pooling function** to further modify the output.

**Pooling** replaces the output of the network at a certain location with a summary statistics of the nearby outputs. For example, _max pooling_ reports the maximum output within a rectangular neighborhood. Other popular pooling functions include the average of the kernels' values, or a weighted average based on the distance from the central pixel. In these cases, _pooling makes the representation invariant to small changes in the input_. If we pool over the outputs of separately parameterized convolutions, the features can learn which transformations to become invariant to.

For many tasks, _pooling is essential for handling inputs of varying size_. By varying the size of an offset between pooling regions, the classification layer will always receive the same number of summary statistics regardless of the input size. For example, the final pooling layer of a network may be defined to output four sets of summary statistics, one for each quadrant of an image _regardless of image size._

## Example of Architectures for Classification with connections

**Left:** This CNN alternates between convolution and pooling for a few layers, and then reshapes the resulting feature map to 'flatten' the spatial dimensions. The remainder of the network is an ordinary feedforward network classifier.

**Center:** This CNN processes a variably sized image but maintains a fully connected section by using a pooling operation with variably sized pools.

**Right:** This CNN outputs one feature map per class in the data (no fully connected layer).

![Examples](https://www.google.com/url?sa=i&source=images&cd=&ved=2ahUKEwjj7trl-srgAhUD_4MKHfMxCm4QjRx6BAgBEAU&url=https%3A%2F%2Fslideplayer.com%2Fslide%2F13751965%2F&psig=AOvVaw0ghLgWi-UhMZsoklB1FSmL&ust=1550774352743094)
