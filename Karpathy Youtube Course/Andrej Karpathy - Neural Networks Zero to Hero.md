Backpropagation - fine tuning weights of neural net based on error rate

https://youtu.be/VMj-3S1tku0?si=7V1YSiIN4qT4tgPx&t=4645

He creates a value container class that has implementations for addition and subtraction.  When these operations are performed with objects of this class, the source values are and operation are stored off.  This can then be used to generate a graph of the solving of a problem.

Having a graph of the whole operation simplifies the process of calculating the derivitive of the end result with respect to any child variable.

These values can represent the weights of a neural network.  Backpropogation is the process of going back and calculating the values from the end result.

With calculus chain rule, derivitive of dL / dc = (dL/dd) * (dd/dc) Finding the derivitive of smaller steps and multiplying them together.  Flowing backwards through the graph of calculations, this allows us to calculate dL/dx for any x earlier in the graph.

L is Loss function, **what is loss function**?

Neuron:
is
![[Pasted image 20240210160952.png]]

x = inputs, w = weights, b = added bias of the neuron

SideNote, might want to learn more about logarithms, euler's number, understand hyperbolic functions more
https://en.wikipedia.org/wiki/Hyperbolic_functions

Derivitive of result output with respect to weight values is most valuable as that is what is changed for optimization

Neural net is a connection of many neurons such as this.
Eventually a loss function is used to determine accuracy of the neural net, and we backpropogate wrt the accuracy.

Machine Learning library will create a number of neurons to run the same input data through.

  

Each layer is n neurons being fed the same data.

Adding an additional layer replicates the neurons with the output from the prior layer

  

Loss can be calculated by comparing MLP out put to groundtruth/expected values.

  

When final output is loss, backpropagating it to initial weights can produce a gradient for the loss wrt the weights and bias value. This information allows self-correction of the weights to get the loss to 0.

  

  

Forward pass goes through net and calculates output values based in inputs(and weights/bias)

Backward pass goes back through results to find gradients/derivatives of the input values.

By using the loss to tune variable inputs, we can continuously make small updates to inputs to approach 0 loss.

  

Small steps in inputs are preferable, as larger steps will result in overstepping desired values. Smaller steps get closer to desired outputs with smaller error.

  

Due to complexity of loss function, overstepping can cause results to blow up, so smaller steps are important. (example video used step of -0.01 * grad, and saw issues when attempting to increase magnitude to -0.1*grad. Step value also referred to as the learning rate, it's a 'subtle art'. Tuning inputs until near 0 loss is the goal of neural net training.

  

Gradient descent: the process of tuning inputs based on gradient to loss output

  

Since initial grads are adding over repeated calculations, each backward pass should initialize these to 0 so they don't constantly accumulate over multiple runs.

  

  

  

  

May want to dig into topological sorting algorithms. Dependency graph like in video of backpropagation needs to be traversable in a unidirectional fashion before backpropagation can be run.