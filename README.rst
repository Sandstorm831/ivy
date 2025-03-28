.. image:: https://github.com/unifyai/unifyai.github.io/blob/master/img/externally_linked/logo.png?raw=true
   :width: 100%

.. raw:: html

    <br/>
    <div align="center">
    <a href="https://github.com/unifyai/ivy/issues">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/github/issues/unifyai/ivy">
    </a>
    <a href="https://github.com/unifyai/ivy/network/members">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/github/forks/unifyai/ivy">
    </a>
    <a href="https://github.com/unifyai/ivy/stargazers">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/github/stars/unifyai/ivy">
    </a>
    <a href="https://github.com/unifyai/ivy/pulls">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg">
    </a>
    <a href="https://pypi.org/project/ivy-core">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://badge.fury.io/py/ivy-core.svg">
    </a>
    <a href="https://github.com/unifyai/ivy/actions?query=workflow%3Adocs">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/github/workflow/status/unifyai/ivy/docs?label=docs">
    </a>
    <a href="https://github.com/unifyai/ivy/actions?query=workflow%3Atest-ivy">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/github/workflow/status/unifyai/ivy/test-ivy?label=tests">
    </a>
    <a href="https://discord.gg/sXyFF8tDtm">
        <img style="float: left; padding-right: 4px; padding-bottom: 4px;" src="https://img.shields.io/discord/799879767196958751?color=blue&label=%20&logo=discord&logoColor=white">
    </a>
    </div>
    <br clear="all" />

**We’re on a mission to unify all ML frameworks 💥 + automate code conversions 🔄. pip install ivy-core 🚀, join our growing community 😊, and lets-unify.ai! 🦾**

.. raw:: html

    <div style="display: block;" align="center">
        <img width="3%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/empty.png">
        <a href="https://jax.readthedocs.io">
            <img width="12%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/jax_logo.png">
        </a>
        <img width="6%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/empty.png">
        <a href="https://www.tensorflow.org">
            <img width="12%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/tensorflow_logo.png">
        </a>
        <img width="6%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/empty.png">
        <a href="https://mxnet.apache.org">
            <img width="12%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/mxnet_logo.png">
        </a>
        <img width="6%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/empty.png">
        <a href="https://pytorch.org">
            <img width="12%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/pytorch_logo.png">
        </a>
        <img width="6%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/empty.png">
        <a href="https://numpy.org">
            <img width="12%" style="float: left;" src="https://raw.githubusercontent.com/unifyai/unifyai.github.io/master/img/externally_linked/logos/supported/numpy_logo.png">
        </a>
    </div>

.. _docs: https://lets-unify.ai/ivy
.. _Colabs: https://drive.google.com/drive/folders/16Oeu25GrQsEJh8w2B0kSrD93w4cWjJAM?usp=sharing
.. _`contributor guide`: https://lets-unify.ai/ivy/contributing.html
.. _`open tasks`: https://lets-unify.ai/ivy/contributing/open_tasks.html

Contents
--------

* `Overview`_
* `Quick Start`_
* `Background`_
* `Design`_
* `Extensions`_
* `Roadmap`_
* `Contributing`_

Overview
--------

Ivy is an ML framework that currently supports JAX, TensorFlow, PyTorch, and Numpy.
We’re very excited for you to try it out!

Next on our roadmap is to support automatic code conversions between all frameworks 🔄,
and add instant multi-framework support for all open-source libraries with only a few lines of code changed!
Read on to learn more 😊

The docs are split into a number of sub-pages explaining different aspects of why we created Ivy,
how to use it, what we’ve got planned on our roadmap, and how to contribute!
Click on the sub-headings below to check out these pages!

We use 🚧 to indicate that the feature being discussed is in development.
We use ✅ to indicate that it is already implemented!

Check out the docs_ for more info,
and check out our Google Colabs_ for some interactive demos!

🚨 Ivy is still at a relatively early stage of development.
Expect breaking changes and sharp edges until we release version 1.2.0 in the next few weeks!

If you would like to contribute,
please check out our `contributor guide`_,
and take a look at the `open tasks`_ if you'd like to dive straight in! 🧑‍💻

Quick Start
-----------

Ivy can be installed like so: ``pip install ivy-core``
You can immediately use Ivy to train a neural network, using your favorite framework in the background, like so:

.. code-block:: python

    import ivy

    class MyModel(ivy.Module):
        def __init__(self):
            self.linear0 = ivy.Linear(3, 64)
            self.linear1 = ivy.Linear(64, 1)
            ivy.Module.__init__(self)

        def _forward(self, x):
            x = ivy.relu(self.linear0(x))
            return ivy.sigmoid(self.linear1(x))

    ivy.set_backend('torch')  # change to any backend!
    model = MyModel()
    optimizer = ivy.Adam(1e-4)
    x_in = ivy.array([1., 2., 3.])
    target = ivy.array([0.])

    def loss_fn(v):
        out = model(x_in, v=v)
        return ivy.mean((out - target)**2)

    for step in range(100):
        loss, grads = ivy.execute_with_gradients(loss_fn, model.v)
        model.v = optimizer.step(model.v, grads)
        print('step {} loss {}'.format(step, ivy.to_numpy(loss).item()))

    print('Finished training!')

This example uses PyTorch as a backend framework,
but the backend can easily be changed to your favorite frameworks, such as TensorFlow, or JAX.

**Framework Agnostic Functions**

In the example below we show how Ivy's concatenation function is compatible with tensors from different frameworks.
This is the same for ALL Ivy functions. They can accept tensors from any framework and return the correct result.

.. code-block:: python

    import jax.numpy as jnp
    import tensorflow as tf
    import numpy as np
    import torch

    import ivy

    jax_concatted   = ivy.concat((jnp.ones((1,)), jnp.ones((1,))), -1)
    tf_concatted    = ivy.concat((tf.ones((1,)), tf.ones((1,))), -1)
    np_concatted    = ivy.concat((np.ones((1,)), np.ones((1,))), -1)
    torch_concatted = ivy.concat((torch.ones((1,)), torch.ones((1,))), -1)

To see a list of all Ivy methods, type :code:`ivy.` into a python command prompt and press :code:`tab`.
You should then see output like the following:

::

   ivy.Container(                         ivy.general                               ivy.reduce_min(
   ivy.abs(                               ivy.get_device(                           ivy.reduce_prod(
   ivy.acos(                              ivy.get_num_dims(                         ivy.reduce_sum(
   ivy.acosh(                             ivy.gradient_descent_update(              ivy.reductions
   ivy.activations                        ivy.gradient_image(                       ivy.relu(
   ivy.arange(                            ivy.gradients                             ivy.reshape(
   ivy.argmax(                            ivy.identity(                             ivy.round(
   ivy.argmin(                            ivy.image                                 ivy.scatter_nd(
   ivy.array(                             ivy.indices_where(                        ivy.seed(
   ivy.asin(                              ivy.inv(                                  ivy.shape(
   ivy.asinh(                             ivy.layers                                ivy.shuffle(
   ivy.atan(                              ivy.leaky_relu(                           ivy.sigmoid(
   ivy.atan2(                             ivy.linalg                                ivy.sin(
   ivy.atanh(                             ivy.linear(                               ivy.sinh(
   ivy.bilinear_resample(                 ivy.linspace(                             ivy.softmax(
   ivy.cast(                              ivy.log(                                  ivy.softplus(
   ivy.ceil(                              ivy.logic                                 ivy.split(
   ivy.clip(                              ivy.logical_and(                          ivy.squeeze(
   ivy.concatenate(                       ivy.logical_not(                          ivy.stack(            
   ivy.container                          ivy.logical_or(                           ivy.stack_images(
   ivy.conv2d(                            ivy.math                                  ivy.stop_gradient(
   ivy.core                               ivy.matmul(                               ivy.svd(
   ivy.cos(                               ivy.maximum(                              ivy.tan(
   ivy.cosh(                              ivy.minimum(                              ivy.tanh(
   ivy.cross(                             ivy.neural_net                            ivy.tile(
   ivy.cumsum(                            ivy.nn                                    ivy.to_list(
   ivy.depthwise_conv2d(                  ivy.norm(                                 ivy.to_numpy(
   ivy.dtype(                             ivy.one_hot(                              ivy.transpose(
   ivy.execute_with_gradients(            ivy.ones(                                 ivy.unstack(
   ivy.exp(                               ivy.ones_like(                            ivy.variable(
   ivy.expand_dims(                       ivy.pinv(                                 ivy.vector_to_skew_symmetric_matrix(
   ivy.flip(                              ivy.randint(                              ivy.verbosity
   ivy.floor(                             ivy.random                                ivy.where(
   ivy.floormod(                          ivy.random_uniform(                       ivy.zero_pad(
   ivy.backend_handler                    ivy.reduce_max(                           ivy.zeros(
   ivy.gather_nd(                         ivy.reduce_mean(                          ivy.zeros_like(

Background
----------

| (a) `ML Explosion <https://lets-unify.ai/ivy/background/ml_explosion.html>`_
| A huge number of ML tools have exploded onto the scene!
|
| (b) `Why Unify? <https://lets-unify.ai/ivy/background/why_unify.html>`_
| Why should we try to unify them?
|
| (c) `Standardization <https://lets-unify.ai/ivy/background/standardization.html>`_
| We’re collaborating with The `Consortium for Python Data API Standards <https://data-apis.org>`_

Design
------

| Ivy can fulfill two distinct purposes:
|
| 1. Serve as a transpiler between frameworks 🚧
| 2. Serve as a new ML framework with multi-framework support ✅
|
| The Ivy codebase can then be split into three categories, and can be further split into 8 distinct submodules, each of which falls into one of these three categories as follows:

.. image:: https://github.com/unifyai/unifyai.github.io/blob/master/img/externally_linked/design/submodule_dependency_graph.png?raw=true
   :align: center
   :width: 100%

| (a) `Building Blocks <https://lets-unify.ai/ivy/design/building_blocks.html>`_
| Backend functional APIs ✅
| Ivy functional API ✅
| Backend Handler ✅
| Ivy Compiler 🚧
|
| (b) `Ivy as a Transpiler <https://lets-unify.ai/ivy/design/ivy_as_a_transpiler.html>`_
| Front-end functional APIs 🚧
|
| (c) `Ivy as a Framework <https://lets-unify.ai/ivy/design/ivy_as_a_framework.html>`_
| Ivy stateful API ✅
| Ivy Container ✅
| Ivy Array 🚧

Extensions
----------

| (a) `Applied Libraries <https://lets-unify.ai/ivy/extensions/applied_libraries.html>`_ ✅
| Ivy libraries in mechanics, vision, robotics, memory, and other areas
|
| (b) **Builder [page coming soon!]** ✅
| :code:`ivy.Trainer`, :code:`ivy.Dataset`, :code:`ivy.Dataloader` and other helpful classes and functions for creating training workflows in only a few lines of code

Roadmap
-------

| We strongly welcome and encourage contributions from the community as we take on this important journey towards ML framework unification. These posts will explain exactly how you can get involved 🙂
|
| (a) **Standardize [page coming soon!]** 🚧
| Align Ivy with the `Consortium for Python Data API Standards <https://data-apis.org>`_
|
| (b) **Front-Ends [page coming soon!]** 🚧
| Create backend-specific front-ends for each supported ML framework
|
| (c) **Transpiler [page coming soon!]** 🚧
| Verify code conversions work for each back-end and front-end combo
|
| (d) **Ecosystem [page coming soon!]** 🚧
| Add multi-framework support to popular repos with a few lines changed

Contributing
------------

Join our community as a code contributor, and help accelerate our journey to unify all ML frameworks!
Find out more in our `Contributing <https://lets-unify.ai/ivy/contributing.html>`_ guide!

Citation
--------

::

    @article{lenton2021ivy,
      title={Ivy: Templated deep learning for inter-framework portability},
      author={Lenton, Daniel and Pardo, Fabio and Falck, Fabian and James, Stephen and Clark, Ronald},
      journal={arXiv preprint arXiv:2102.02886},
      year={2021}
    }
