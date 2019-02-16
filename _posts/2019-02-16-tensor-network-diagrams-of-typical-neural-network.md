---
layout: post
title:  "Tensor network diagrams of typical neural networks"
categories:
comments: true
mathjax: true
---

In the winter of 2018, I followed a course on tensor network methods for strongly correlated electrons given by Glen Evenbly at Université de Sherbrooke. Basically, the course introduces a diagrammatic notation to write tensor products, and uses it to revisit famous methods of strongly correlated physics, among which the numerical renormalization group (NRG), density matrix renormalization group (DMRG), matrix product states (MPS), multi-scale entanglement renormalization ansatz (MERA), etc.

Since I began working on neural networks, I like to draw the tensor network diagram corresponding to various architecture visited in <a href='https://www.deeplearningbook.org/'>the Deep Learning book</a>. I find the tensor network notation less ambiguous than most others I have encountered so far.

In a near future, I plan to fully describe the notation here, and gather many diagrams. For now simply note that I had to augment the diagrammatic notation to account element-wise products and sums (as teardrop, with the corner indicating the ouptut channel) and also element-wise non-linear activation functions (as black arrowheads with single input/output).

For example, here is my rendition of the tensor network diagram for the long short-term memory (LSTM) recurrent neural network, following the notation of the DL book, p. 399 (or p. 406 online).

<img class="center" src="/img/lstm-01.png"  title="Tensor network diagram for the LSTM" width="400px"/>

Stay tune for more!

