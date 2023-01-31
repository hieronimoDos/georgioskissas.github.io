---
layout: post
title: Learning Operators with Coupled Attention will be presented at the Thirty-sixth Conference on Neural Information Processing Systems 
date: 2022-11-22 15:59:00-0400
inline: false
---

Our paper [Learning Operators with Coupled Attention](https://www.jmlr.org/papers/v23/21-1521.html)  is accepted at the Thirty-sixth Conference on Neural Information Processing Systems via the Journal to Conference track.

***


Supervised operator learning is an emerging machine learning paradigm with applications to modeling the evolution of spatio-temporal dynamical systems and approximating general black-box relationships between functional data.  For example, assume that we want to approximate a map between a temperature field and a pressure field on the surface of the earth for different time instances during a range of years from a limited amount of measurements coming from sources such as satellites and weather stations. Despite having labeled data to a limited amount of spatial locations we want to be able to make predictions at any given location at the surface of the earth. Another desirable property of the model would be to be able to make pressure predictions for different temperature fields without having to retrain the model.  By learning an operator between function spaces, we are able to query an output function at any location for any input sample that comes from the distribution that our model was trained on.

Taking into account the complexity of real-world engineering applications we consider three properties that Operator Learning methods should possess in order to become useful tools:
<ul>
    <li>Data efficiency: Operator Learning methods should be data efficient, meaning that they should be able to provide a small median error and error spreads while being trained using a small number of labeled data.</li>
    <li>Robustness: Operator Learning methods should be robust, in the sense that their accuracy should not be drastically affected if either the testing or both the training and testing datasets are corrupted by noise.</li>
    <li>Generalization: Operator Learning methods should generalize well to a testing dataset and ideally would behave well under small distribution shifts.</li>
</ul>

***

For this purpose, we propose a novel operator learning method, LOCA (Learning Operators with Coupled Attention), motivated from the recent success of the attention mechanism. In our architecture, we first create a feature embedding of the input functions through the wavelet scattering transform which is known to be robust to small deformations and corruption by noise.  These fixed features are passed through an MLP to create the final input feature embedding.  Then, for each location in the output function domain, attention weights are generated to average the input features with.  A key component of the model is the introduction of a kernel transform which couples these attention weights to each other over the output query domain.  By coupling these attention weights together with an integral transform, LOCA is able to explicitly learn correlations in the target output functions, enabling us to approximate nonlinear operators even when the number of output function measurements in the training set is very small.  For the final step the finite feature encoding is averaged with attention weights to make predictions of the expected value of the function at the query location of interest.

Our formulation is accompanied by rigorous approximation theoretic guarantees on the universal expressiveness of the proposed model.
Empirically, we evaluate the performance of LOCA on several operator learning scenarios involving systems governed by ordinary and partial differential equations, where our goal is to approximate a map between some random initial or boundary condition and the resulting output function,  as well as a black-box climate prediction problem like the one we talked in the start where our goal is to map surface air temperature to surface air pressure for different time instances across the whole earth surface. Through these scenarios we demonstrate state of the art accuracy, robustness with respect to noisy input data, and a consistently small spread of errors over testing data sets, even for out-of-distribution prediction tasks.
