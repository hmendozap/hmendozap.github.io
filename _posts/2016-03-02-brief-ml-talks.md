---
layout: post
title: Brief Talks for University of Freiburg's ML Professorship
hide: false
---

I haven't had much opportunity to update the blog because well, I'm working on my master thesis, which by the way is developing into a nice project with more research for the future.

With the growing importance of Machine Learning (ML) in the academy and the industry there are many big changes. "Recently" the University of Freiburg had the opening of a Professorship for ML in the Technical Faculty. As a part of the application, each candidate must give a 45-minute presentation of their most important work. Thankfully being an open process the students can attend to them.

Next I will summarize what I belive were the most important points of each talk. 

## Probabilistics Numerics
by: [Phillip Henning](https://ei.is.tuebingen.mpg.de/person/phennig) from [Empirical Inference (IMP)](https://ei.is.tuebingen.mpg.de/) in Tübingen

His main point was to point to make calculations based on probabilistic model and how these are related or are equivalent to more known numerical analysis methods for differentiation, optimization, linear algebra and quadratures. According to Prof. Henning these are:

- GP Regression <--> Gauss Quadrature

- Conjugate Gradient <--> Gauss Conditioning

- BFGS/Quasi-Newton Methods <--> Autoregessive Filter

-  Runge-Kutta Methods <--> Gauss-Markov Extrapolation

Probabilistic models certainly have advantages in that they effectively incorporate uncertainty and also informative priors.

Prof. Henning next discussed one important research done by its group on using probabilistic numerics to correctly set hyperparameters on ML Algorithms on the [_"Probabilistic Line Search"_](http://arxiv.org/abs/1502.02846) then presented that performance of Neural Networks' (NN) after setting the _learning rate_ using the algorithm described on the paper. Certainly using probabilistic line search improves NN on MNIST classification from the get go. (To be honest I only skimmed the paper, but it seems very alluring)

The ideas presented by Prof. Henning are, from my point of view, very, very interesting: from the ability to approximate integrals with uncertainty or to efficiently set hyperparameters of ML algorithms, which is truly promising to complement the AutoML research.

## Visual Inference
by: [Peter Gehler](http://files.is.tue.mpg.de/pgehler//), also from Tübingen

As his webpage states, his main investigation is: _"Trying to learn how to learn to see"_. Basically we know how to accurately simulate images, and using this with information about depth or hue we try to infer a physical understanding of the world.

To give a more concrete example I redirect you to one study of Dr. Gehler, where the idea was given a depth image, infer the body shape. [_"The informed sampler: A discriminative approach to Bayesian inference in generative computer vision models"_](https://ps.is.tuebingen.mpg.de/uploads_file/attachment/attachment/260/jampani2015informedsampler.pdf).

Dr. Gehler then extended about bilateral filtering as high dimensional filtering. Basically this filter allows to maintain information about the edges and information about the structure while reducing memory and processing resources. In my personal opinion that is big! If you read the [paper](https://ps.is.tuebingen.mpg.de/publications/jampani-cvpr-2016) you can notice the improvement on performance over the famously known AlexNet and Convolutional Neural Network.

The ideas presented by Dr. Gehler have a real and present application, they make an interesting case for the need of an expert at the time of constructing ML algorithms. It brings an interesting need to how visual information is processed, instead of looking only at pixels, algorithms should also look at context.

## Nonlinear Spectral Methods for Clustering and Deep Learning
by: [Matthias Hein](http://www.ml.uni-saarland.de/people/hein.htm), from Saarland University

This one for me was the most fascinating talk and another reason for which I complained to my younger self for not studying a bachelor in Mathematics.

Prof. Hein's research is mainly focused on methods for [efficient clustering of graphs](http://www.ml.uni-saarland.de/code/pSpectralClustering/pSpectralClustering.htm). His group devised an optimal and efficient learning of combinatorial factorial programs (optimizations), namely the cheeger cut problem, where one tries to make the least amount of division in a graph while maintaining high consistency or similarity in the groups.

They found an optimal solution using something called [RatioDCA](http://arxiv.org/pdf/1312.5192v2.pdf), which is solved by using homogeneous transformations on Linear Eigen Problems. (From my basic understanding is the ratio between a transformation of the subset, aka the cut of the graph and a transformation of the whole graph)

He then continued with the current research done on NN, which aims to optimally solve the parameters of a Polynomial NN (one that its activation function are polynomial functions). This current approach gives some promising results but not entirely convincing.

The ideas presented by Prof. Hein are adventurous and tempting, it approaches the ML problems from a very geometric/topological point of view, which for me could either be a huge advance or a refreshing addition to ML research.

## AutoML
by: [Frank Hutter](http://aad.informatik.uni-freiburg.de/people/hutter/index.html), from [University of Freiburg](http://aad.informatik.uni-freiburg.de/)

Automated ML is that a ML learning algorithm is aware of its performance and changes its configuration in order to improve such performance. Dr. Hutter's main idea is developing AutoML using Bayesian Optimization. Using this approach the group has remained champion on the AutoML challenge. The tool is called [auto-sklearn](https://github.com/automl/auto-sklearn/tree/development) for those of you interested. 

Dr. Hutter then continued with applications of random embeddings on bayesian optimization, i.e. discard unnecessary dimensions, and with advances on working Entropy Search, a collaborative project with Dr. Henning, which an iterative work, of starting with small data, finding a good place to optimize and then expanding the amount of data and places for where to improve performance.

There's current work done on using these techniques on NN and other fields as robotics and the latest use case was when AutoML helped solved SAT problems for the FCC, in the [auctioning of spectrum](http://www.cs.ubc.ca/labs/beta/Projects/SATFC/papers/SATFC.pdf).

The ideas presented by Dr. Hutter are the basis for the AutoML research community and an important column for the increasing public use of ML algorithms. Advancing and studying behavior of algorithms that are already deployed on tools as Siri, or fraud detection are as important as the algorithm itself.

### Conclusion

This were four of the eight talks carried out by the University of Freiburg as part of the process of nominating candidates to ML Professorship in the state of Baden-Württemberg. Each one has its special appeal that makes the choice much harder, but as my professor said: **"Anyone that ends up in here will be a good addition to the University"**

**DISCLAIMER**: Sorry if I misunderstood the theory, I have tried my best to write this summary.