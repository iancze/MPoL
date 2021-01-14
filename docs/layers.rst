RML with layers
===============

A significant computational development, driven by the rise in machine learning and deep neural networks, is the development of autodifferentiation. 

Autodifferentiation is a fast-evolving field, so currently we're based on PyTorch. That may change as the autodifferentiation and neural network landscape develops, i.e., Jax.

MPoL is designed such that there is flexibility, so are perfectly capable of using it without the neural network features. However, it is worthwile to briefly overview some of the concepts since it helps explain the organization of the code. 

Layers 
------

Input and Output connections.

For example, in the very simple case of linear regression, we have a model of 

y = mx + b 

and a dataset with some y points, some x points. The model has parameters m, b. We could do a prediction with the model, which would be evaluating the y model points. 

The idea is we can create a "loss function" describing the distance from the prediction to the model. To keep things in the same terms as a typical chi^2 fitting example, we'll use a L2 norm. 

Normally (at least these days in astronomy), we'd phrase this as a Bayesian inference problem where we're interested in the posterior distribution p(m, b | data). 

But, in theory there are a lot of different loss functions we could use, which we'll return to shortly in the context of RML.

Alternatively, this could be phrased as a neural network with a layer that connects the inputs x to the outputs y. There are many resources (link) providing references to these. 

You can think of the posterior distribution as a surface. We'll depart from Bayesian terminology and simply call this a "loss surface." So we'll use the optimization to achieve the maximum a posteriori set of parameters. Or, in the case of no regularizers or priors, we would find the maximum likelihood solution. But we have regularized it, so it's the regularized maximum likelihood.

RML imaging as interconnected layers 
------------------------------------

As discussed in the introduction, we think it helps to consider RML imaging as a forward modeling problem, as opposed to an image deconvolution problem.

Starting from the simplest sense, we have an image layer, connected to a fourier transform layer, trained to the data. 

We have the idea of a gridded and ungridded Fourier layer. The Fourier layer has a "predict" data, or predict image? It depends on which way we want to go and what's the core layer.

Let's make an annular ring. 

What specifies the image layer? Well, it could be a parametric model. So, we'll try the case of a Gaussian source. We have a Gaussian model, has inputs size, location, etc. This works well when we have reason to believe the data is generated from this model.

What about when it isn't? Can we do a blend between a parametric and non-parametric model? Gaussian ring w/ off-centered ALMA logo? Can we enforce sparsity to put as much weight (amplitude) as possible on the parametric model and as little on the non-parametric as possible?

Alternatively, we can make the problem completely non-parametric. The simplest form is to represent the sky brightness distristibution using a set of image pixels. We call this an image layer.

But, we don't actually need to represent it with pixels, there are likely other forms that would be worthwhile. I.e., an autoencoder basis. Or whatever.

Image optimization as training 
------------------------------

Following on from the layer discussion, and the relationship to Bayesian inference, the idea is that there is some set of parameters that maximize the posterior. 

One approach would be to combine all of the data into a single container, and just train/optimize off  of that. 

But let's say you had a combination of multiple datasets, from different telescope and there was an unknown calibration factor for each telescope.

This approach would be to "batch" the data in the training loop, and train in each step. This training loop is commonly to other neural network architectures. 