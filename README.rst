SageMaker Scikit-Learn Extension
================================

SageMaker Scikit-Learn Extension is a Python module for machine learning built on top of `scikit-learn <https://scikit-learn.org>`_.

This project contains standalone scikit-learn estimators and additional tools to support SageMaker Autopilot. Many of the additional estimators are based on existing scikit-learn estimators.


User Installation
-----------------

To install,

::

    # install from pip
    pip install sagemaker-scikit-learn-extension

In order to use the I/O functionalies in the :code:`sagemaker_sklearn_extension.externals` module, you will also need to install the :code:`mlio` package via conda. The :code:`mlio` package is only available through conda at the moment.

To install :code:`mlio`,

::

    # install mlio
    conda install -c mlio -c conda-forge mlio-py

You can also install from source by cloning this repository and running a ``pip install`` command in the root directory of the repository:

::

    # install from source
    git clone https://github.com/aws/sagemaker-scikit-learn-extension.git
    cd sagemaker-scikit-learn-extension
    pip install -e .


Supported Operating Systems
---------------------------

SageMaker scikit-learn extension supports Unix/Linux and Mac.

Supported Python Versions
-------------------------

SageMaker scikit-learn extension is tested on:

- Python 3.7

License
-------

This library is licensed under the Apache 2.0 License.

Development
-----------

We welcome contributions from developers of all experience levels.

The SageMaker scikit-learn extension is meant to be a repository for scikit-learn estimators that don't meet scikit-learn's stringent inclusion criteria.


Setup
-----

We recommend using conda for development and testing.

To download conda, go to the `conda installation guide <https://conda.io/projects/conda/en/latest/user-guide/install/index.html>`_.


Running Tests
-------------

SageMaker scikit-learn extension contains an extensive suite of unit tests.

You can install the libraries needed to run the tests by running :code:`pip install --upgrade .[test]` or, for Zsh users: :code:`pip install --upgrade .\[test\]`

For unit tests, tox will use pytest to run the unit tests in a Python 3.7 interpreter. tox will also run flake8 and pylint for style checks.

conda is needed because of the dependency on mlio.

To run the tests with tox, run:

::

    tox

Running on SageMaker
--------------------

To use sagemaker-sklearn-extension on SageMaker, you can build the `sagemaker-autopilot-container <https://github.com/aws/sagemaker-scikit-learn-container>`_.

Overview of Submodules
----------------------

* :code:`sagemaker_sklearn_extension.decomposition`
   * :code:`RobustPCA` dimension reduction for dense and sparse inputs
* :code:`sagemaker_sklearn_extension.externals`
   * :code:`AutoMLTransformer` utility class encapsulating feature and target transformation functionality used in AutoML pipelines
   * :code:`Header` utility class to manage the header and target columns in tabular data
   * :code:`read_csv_data` reads comma separated data and returns a numpy array
* :code:`sagemaker_sklearn_extension.feature_extraction.text`
   * :code:`MultiColumnTfidfVectorizer` convert a many collections of raw documents to a matrix of TF-IDF features.
* :code:`sagemaker_sklearn_extension.impute`
   * :code:`RobustImputer` imputer for missing values with customizable mask_function and multi-column constant imputation
   * :code:`RobustMissingIndicator` binary indicator for missing values with customizable mask_function
* :code:`sagemaker_sklearn_extension.preprocessing`
   * :code:`ExtremeValueTransformer` transformer for columns that contain "extreme" values (columns that are heavy tailed)
   * :code:`QuadraticFeatures` generate and add quadratic features to feature matrix
   * :code:`ThresholdOneHotEncoder` encode categorical integer features as a one-hot numeric array, with optional restrictions on feature encoding
   * :code:`RobustLabelEncoder` encode labels for seen and unseen labels
   * :code:`RobustStandardScaler` standardization for dense and sparse inputs