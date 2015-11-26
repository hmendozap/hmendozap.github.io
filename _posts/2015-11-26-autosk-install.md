---
layout: post
title: Autosk-Learn Installation
---

This one in english and assumes that you have knowledge with unix terminal, github, python virtual environments and pip.

I've just started my Master's Thesis with the awesome group of Prof. Frank Hutter's [Algorithm Configuration](http://aad.informatik.uni-freiburg.de/) and one of my tasks is to run the [autosk-learn](https://github.com/automl/auto-sklearn) tool. Until now is still a little bit cumbersome to achieve this, so I will detail the installation process that **worked for me**.


---

### Introduction

For those of you who want to know what [_autosk-learn_](http://auto-sklearn.readthedocs.org/en/master/) is:

> _auto-sklearn_ is an automated machine learning toolkit and a drop-in replacement for a scikit-learn estimator.

Basically [scikit-learn](http://scikit-learn.org/stable/) (a library with lots and lots of machine learning [ML] algorithms) needs to have a _configuration setting_ that is the parameters or constants that configure the algorithm, e.g. the number of trees in **random forests**.

But how to get the right value for each parameter? Well, there's where auto-sklearn, comes in handy and more. This process is called [**Hyperparameter Optimization**](http://www.cs.ubc.ca/labs/beta/Projects/SMAC/papers/11-LION5-SMAC.pdf) that uses bayesian optimization (not a must, but BO is better at this [task](http://aad.informatik.uni-freiburg.de/papers/13-BayesOpt_EmpiricalFoundation.pdf)) in order to calculate the _best_ values of these parameters for each algorithm. (I'm super simplifying things, but it's good enough)

---

### Installation

Anyways, let's get down to business. First we create a _semi-new_ virtual environment on python (It must contain numpy and scipy), then we start adding the necessary dependencies:

First scikit-learn version 0.16, because _auto-sklearn_ has been developed for at least 10 months, this is the scikit release we've been working on:

~~~
pip install scikit-learn==0.16.1
~~~

Then we install [HPOlib](https://github.com/automl/HPOlib), [HPOlibConfigSpace](https://github.com/automl/HPOlibConfigSpace) and [ParamSklearn](https://github.com/automl/paramsklearn.git@development
):

~~~
pip install git+ssh://git@github.com/automl/HPOlib.git --no-deps
pip install git+ssh://git@github.com/mfeurer/HPOlibConfigSpace.git
pip install git+ssh://git@github.com/automl/paramsklearn.git@development
~~~

We continue with the others dependencies:

~~~
pip install liac-arff
pip install lockfile
pip install joblib
pip install psutil
pip install pyyaml
pip install pandas==0.16.2
pip install protobuf
pip install Cython
pip install setuptools
pip install mock
~~~

And we finally install the auto-sklearn:

~~~
pip install git+ssh://git@github.com/automl/auto-sklearn.git#egg=autosklearn --no-deps
~~~

That's it! We have installed one powerful tool for algorithm auto-configuration. To continue with development check the auto-sklearn docs!

### Happy auto config!!