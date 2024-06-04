# Activation Functions

## Sigmoid

- defined: $\sigma(x) = \frac{1}{1 + e^{-x}}$
- features:
  - squashes the input into the range [0, 1]
  - used in output layer for binary classification
- drawbacks:
  - vanishing gradient problem
  - output is not zero-centered
- derivative: $\sigma'(x) = \sigma(x)(1 - \sigma(x))$
  
## Tanh

- defined: $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}$
- features:
  - squashes the input into the range [-1, 1]
  - used in hidden layers
- drawbacks:
  - vanishing gradient problem
  - output is zero-centered
- derivative: $\tanh'(x) = 1 - \tanh^2(x)$

## ReLU

- defined: $\text{ReLU}(x) = \max(0, x)$
- features:
  - simple and computationally efficient
  - output is zero for negative inputs
- drawbacks:
  - dying ReLU problem
  - output is not zero-centered
- derivative: $\text{ReLU}'(x) = 1$ if $x > 0$ else $0$

## Leaky ReLU

- defined: $\text{LeakyReLU}(x) = \max(0.01x, x)$
- features:
  - $0.01$ is a hyperparameter
  - addresses the dying ReLU problem
  - output is zero for negative inputs
- drawbacks:
  - output is not zero-centered
- derivative: $\text{LeakyReLU}'(x) = 1$ if $x > 0$ else $0.01$

## Softmax

- defined: $\text{Softmax}(x_i) = \frac{e^{x_i}}{\sum_{j=1}^{n} e^{x_j}}$
- features:
  - squashes the input into the range [0, 1]
  - used in output layer for multi-class classification
  - output is a probability distribution
  - ensures that the sum of the probabilities is 1
- drawbacks:
  - vanishing gradient problem
  - output is not zero-centered
  - sensitive to outliers
- derivative: $\text{Softmax}'(x_i) = \text{Softmax}(x_i)(1 - \text{Softmax}(x_i))$