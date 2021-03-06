The Hyperparameter Optimization Problem
=======================================

When working with a machine learning algorithm (e.g., Decision Trees, KNN, SVM,
MLP, Convolutional Neural Nets, etc.), you will come across values supplied to
the algorithm that affect how well it can learn from your data. Usually, these
are passed as arguments to the function or class that implements the algorithm.
These are *hyperparameters*, and properly tuning them can mean the difference
between success and failure. This is called *hyperparameter optimization*.

Optimizing hyperparameters involves searching over the range of possible
hyperparameter values (and combinations of values) for the one that leads to
the best performance on your dataset. For example, when working with KNN you
must select the value *k* (the number of nearest neighbors); for SVM with RBF
kernel, you must pick values for the *C* (soft-margin constant) and :math:`\gamma`
(kernel coefficient); a neural network requires tuning many values at each layer.
The catch with hyperparameter optimization is that it's a **nonlinear,
non-convex optimization problem**. This means that there is no perfect set of
hyperparameter values, and using gradient-based methods can get you stuck in the
wring place. "Optimal" in this case means "the best that can be found
experimentally": you have to test a lot of values over a wide range to make sure
you picked good ones. A good primer on this problem that goes into more detail
can be found in [1]_.

Optimal hyperparameters can mean the difference between just a few percentage
points better performance, but in many cases it can change a failing model into
a successful one. With so many possible choices, though, how do you select the
optimal values?

By Hand
-------

A lot of times, hyperparameter optimization is done by hand. This method is
pretty easy to implement, but it typically misses a lot of possible search values.

Grid Search
-----------

An easy automated search is over a grid of values, with one dimension in the
grid for each hyperparameter. Grid search is also pretty easy to implement, but
when you're searching real-valued hyperparameters, you'll also miss a lot of
values between the grid spaces.

Random Search
-------------

Randomly searching values from a pre-defined (discrete) set or (continuous) range
is just about as easy to implement as grid search, and it can plug the holes in
the grid. Bergstra and Bengio demonstrated in [1]_ that random search
is in general more successful than grid search. Most hyperparameter optimization
software, including SHADHO, implements this method. In fact, this is what SHADHO
does by default!

Bayesian Optimization
---------------------



Remarks
-------

There are a lot of ways to do hyperparameter optimization, and no one method is
correct for every problem. If your hyperparameter values can be enumerated and
exhaustively searched, then grid search may be the correct solution. Random search
is especially useful if you have a large number of continuous parameters to tune.
SHADHO will strive to provide implementations of these and other hyperparameter
search strategies.

References
----------

.. [1] `Bergstra, J., & Bengio, Y. (2012). Random search for hyper-parameter optimization. Journal of Machine Learning Research, 13(Feb), 281-305. <http://www.jmlr.org/papers/volume13/bergstra12a/bergstra12a.pdf>`_
