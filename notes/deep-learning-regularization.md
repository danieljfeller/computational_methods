Many strategies are used in machine learning to __reduce the test error while potentially increasing the training error__.  These strategies are known collectively as **regularization** and __only used to prevent model overfitting__. Regularization is defined as _any modification we make to a learning algorithm that is intended to reduce its generalization error but not its training error._

### Parameter Norm Penalties
Many regularization approaches are based on limited the capacity of models. This is achieved by adding a parameter norm penalty to the objective function that effectively _penalizes (shrinks) the weights of the model_.

**L2 regularization** (aka ridge regression) is an example of _weight decay_ that drives model parameters closer to the origin by adding a regularization term to the objective function.

**L1 regularization** optimizes some parameters to zero. This results in more _sparsity_ compared to L2 regularization and is often used as a _feature selection_ mechanism.

### Dropout Regularization
**Dropout** is the _(seemingly crazy!)_ process of randomly removing nodes in our neural network. Essentially, dropout ensures that we cannot rely on any one feature and instead expand our model to include many weights _thereby shrinking weights like a L2 norm penalty_.  

This most common technique is called **inverted dropout**. We create a vector of random numbers _of the same size as a given layer_ that asserts whether to retain or remove each node in the layer.

Practical Considerations.
1. Not common to perform dropout on input layer (but it _is_ applied, use a dropout probability of 0.9).
2. While sometimes it will benefit performance to assign a different probability of dropout to each layer in the network, this requires that you search for more hyper-parameters using cross-validation.
3. Like other regularization methods, **dropout is only useful when you are overfitting the data**
