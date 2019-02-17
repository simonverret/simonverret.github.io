---
layout: post
title:  "Tensor network diagrams of typical neural networks"
categories:
updated: 2019-02-17
comments: true
mathjax: true
---






The starting point of all neural network is the following operation on input $\vec x$:
\begin{align}
h_{i}=g\left(\sum_{j}W_{ij}x_{j}+b_{i}\right)
\label{oneLayer}
\end{align}
where $\vec h$ is the ouput vector of the layer, $\vec W$ is the matrix of weights, $\vec b$ is the vector of offsets, and $g(z)$ is the activation function, typically a <a href='https://en.wikipedia.org/wiki/Rectifier_(neural_networks)'>ReLU gate</a>, a <a href='https://en.wikipedia.org/wiki/Sigmoid_function'>sigmoid function</a>, or a tanh function.
For $l$ layers, the final output of the network would be the output of the last layer $\vec y=\vec h^{(l)}$.
In the <a href='https://www.deeplearningbook.org/'>the Deep Learning book</a>, the above equation is pictured as:
<img class="center" src="/img/neuralTensorNetwork-01.png"  title="diagrammatic representation of one neural network layer" width="800px"/>
with the weights, offsets, and activation function implicit. Within this diagrammatic convention, here is what a fully connected $l$ layers neural network, or ``multi-layer perceptron'' (MLP), looks like:
<img class="center" src="/img/neuralTensorNetwork-02.png"  title="diagrammatic representation of a fully connected MLP" width="800px"/>

<br>

Problems of these diagrams
---
To be quite honest, I do not like this diagrammatic convention, because you need to know the equations represented to be able to understand the diagram. A good example is when the reccurent neural network (RNN) is introduced:
<img class="center" src="/img/deepLearningBook-10-3.png"  title="diagrammatic representation of a RNN" width="800px"/>
At first glance, the reader might understand that $\vec U$ and $\vec W$ are weights applied respectively on the input $x^{(t)}$ recieved at time $t$ and hidden state $h^{(t-1)}$ computed at time $t-1$. The reader can then infer that they might have respective offsets $\vec b$, but what happens exactly to the results of these two? are they added, multiplied or concatenated to form $h^{(t)}$? Are they separately passed into a non-linear gate? Although the picture makes it unclear, a rapid glace at the equations:
\begin{align}
\vec a^{(t)} &= \vec b + \vec W\vec h^{(t-1)} + \vec U\vec x^{(t)}\\\ 
\vec h^{(t)} &= \tanh(\vec a^{(t)})\\\
\vec o^{(t)} &= \vec c + \vec V\vec h^{(t)}
\end{align}
not only answers that they are added, and then the result is passed to the non-linear gate, we now also know it is a tanh gate. Moreover, two offsets are unnecessary in this context; only one is needed. In short, the diagrammatic notation cannot be directly translated to the maths. I consider this a big prolem compared, for example, to Feynmann diagrams, which becam famous and widely used mainly because they translate directly to equations.

<br>

Tensor network notation in physics
---
In the winter of 2018, I followed a course on tensor network methods for strongly correlated electrons given by Glen Evenbly at Université de Sherbrooke. Basically, the course introduces a diagrammatic notation to write tensor products, and uses it to revisit famous methods of strongly correlated physics, among which the numerical renormalization group (NRG), density matrix renormalization group (DMRG), matrix product states (MPS), multi-scale entanglement renormalization ansatz (MERA), etc.

Here are the basics: vector have one leg (because they have one index), matrix have two, and more general tensors have as many as their rank. You can then illustrate a tensor product by connecting the legs corresponding to the index summed.
<img class="center" src="/img/neuralTensorNetwork-03.png"  title="basics of the tensor network notation" width="800px"/>

Since I began working on neural networks, I always try to draw the tensor network diagram corresponding to various architecture visited in <a href='https://www.deeplearningbook.org/'>the Deep Learning book</a>. I try to clean it of all ambiguity. For example, here is the representation of a simple hidden unit using a sigmoid gate $\sigma(z)$:
\begin{align}
h_{i}=\sigma\left(\sum_{j}W_{ij}x_{j}+b_{i}\right)
\end{align} 
which can be depicted with the two equivalent diagrams (to show that the orientation of the elements are not important):
<img class="center" src="/img/neuralTensorNetwork-04.png"  title="tensor network diagram for a single hidden unit" width="800px"/>
Here is how the deep neural network illustrated at the beginning would look like:
<img class="center" src="/img/neuralTensorNetwork-05.png"  title="tensor network diagram for a deep MLP" width="800px"/>
with $g^{(k)}$ telling what non-linearity is used at each layer. Note that I had to add element-wise operations to the notation, illustrated as teardrops with their corner indicating the ouput of the operation. I also augmented the notation with arrowheads to represent non-linear functions.

<br>

Tensor network notation for (RNN)
---
Here are more diagrams. I plan to add more descriptions in the near future, but you should nevertheless be able to read most of them right away.

Here is a RNN's hidden unit; DL book equation 10.8-10.9:
<img class="center" src="/img/neuralTensorNetwork-06.png"  title="tensor network diagram for the hidden unit of a RNN" width="800px"/>
Here is a full RNN, DL book equation 10.8-10.10:
<img class="center" src="/img/neuralTensorNetwork-07.png"  title="tensor network diagram a basic RNN" width="800px"/>
The same, but unfolded:
<img class="center" src="/img/neuralTensorNetwork-08.png"  title="tensor network diagram of an unfolded RNN" width="800px"/>
The internal state of a long short-term memory unit (LSTM); DL book equation 10.41:
<img class="center" src="/img/neuralTensorNetwork-09.png"  title="Tensor network diagram for the LSTM" width="800px"/>
The full LSTM; DL book equations 10.40-10.44:
<img class="center" src="/img/neuralTensorNetwork-10.png"  title="Tensor network diagram for the LSTM" width="800px"/>
Stay tuned for more!

