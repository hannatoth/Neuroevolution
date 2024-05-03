neural Architecture Search

🌼 Project description  
- The project addresses the problem of optimizing the configuration of a
neural network model for image classification. Specifically, the aim is to find the optimal
set of parameters, for a convolutional neural network. Given the vast number of possible
configurations, manual tuning is a laborious and often impractical process. This challenge
calls for an automated, intelligent approach to hyperparameter tuning. This study
employs an evolutionary algorithm (EA) - a type of algorithm inspired by natural
selection and evolution - to tackle this task.
- The process begins with a randomly generated population. For each generation, a subset
is selected to produce offspring through recombination and mutation. Recombination
combines the "genes" of two parent configurations to create a new one, while mutation
introduces small, random changes into a configuration. The fittest individuals from the
combined population of parents and offspring are then selected to proceed to the next
generation. This process is repeated for 20 generations, with the population gradually
evolving.  

🌼 Problem Statement

The configuration of a CNN, including the number and size of convolutional kernels, the
types of activation functions, the number of neurons in the hidden layer, and others, can
significantly influence the model's performance. Therefore, the problem at hand can be
viewed as a function minimization problem, where the function to be minimized is the
objective function representing the error or loss of the CNN model.
The specific objective function utilized in this study is cross-entropy loss, a commonly
used measure for classification tasks. In the context of image classification, the true
distribution assigns a probability of 1 to the correct class and 0 to all other classes, while
the predicted distribution is output by the model. The aim is to adjust the model's
parameters to minimize this loss, which equates to maximizing the model's prediction
accuracy.

🌼 Methodolgy

The model must minimize the discrepancy between its predictions and the actual values, as
quantified by the cross-entropy loss function. Cross-entropy loss is given by the formula:
**L = -Σ [y log(p) + (1 - y) log(1 - p)]** where 'y' is the actual value, and 'p' is the model's
predicted probability. The problem is broken down into two main phases: 
 - 1 hyperparameter optimization using an Evolutionary Algorithm
 - 2 the training of the neural network model itself.
The EA operates on a population of candidate solutions. Each candidate is a potential set
of hyperparameters for the model, such as the kernel size and the number of kernels in the
convolutional layer, and the number of neurons in the fully connected layer. The EA uses
mechanisms inspired by biological evolution, such as selection, recombination (crossover),
and mutation, to evolve the population over generations.

Each neural network model is designed with a specific architecture. This includes a
convolutional layer with a kernel size and a number of kernels determined by a genetic
algorithm, an activation function chosen from ReLU, Sigmoid, Tanh, Softplus, and ELU, a
pooling layer chosen from Average Pooling, Max Pooling or Identity, a fully connected
hidden layer with a number of neurons determined by a genetic algorithm, and an output
layer that uses a LogSoftmax activation function.


🌼 Experiments  


The architecture of the model is built dynamically based on the hyperparameters
provided. In our case, the hyperparameters include:
 - Number of convolutional kernels: Chosen from the set {8, 16, 32} based on the first
position of the genetic encoding.
-  Convolutional kernel size: Either 3x3 or 5x5 based on the second position of the genetic
encoding.
-  Convolutional layer activation function: One of ReLU, Sigmoid, Tanh, Softplus, or ELU,
chosen based on the third position of the genetic encoding.
-  Pooling layer type: Either Average or Max pooling based on the fourth and fifth
positions of the genetic encoding. If the fourth position encodes a '1', no pooling is
applied.
-  Number of neurons in the hidden layer: A value from 10 to 100 (in steps of 10) based on
the sixth position of the genetic encoding.
 - Hidden layer activation function: One of ReLU, Sigmoid, Tanh, Softplus, or ELU,
chosen based on the seventh position of the genetic encoding.


🌼 Results and discussion

The results of the comparisons indicate that the EA - optimized network significantly outperformed
both MLP and CNN models. Specifically, there is a significant reduction in both NLL and test classification error on the test set when comparing the
current results to the previous models. This improvement suggests that the best performing network exhibits better
generalization and predictive capabilities. It can more accurately classify and predict
unseen data, resulting in lower errors and a more reliable estimation of the model's
uncertainty.
