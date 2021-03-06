<div align="center">
  <img src="docs/_static/logo.png" alt="prince_logo"/>
</div>

<br/>

<div align="center">
  <a href='http://prince.readthedocs.io/en/latest/?badge=latest'>
    <img src='https://readthedocs.org/projects/prince/badge/?version=latest' alt='Documentation Status' />
  </a>
  <a href="https://badge.fury.io/py/prince">
    <img src="https://badge.fury.io/py/prince.svg?style=flat-square" alt="PyPI version"/>
  </a>
  <a href="https://travis-ci.org/MaxHalford/Prince?branch=master">
    <img src="https://travis-ci.org/MaxHalford/Prince.svg?branch=master&style=flat-square" alt="Build Status"/>
  </a>
  <a href="https://coveralls.io/github/MaxHalford/Prince?branch=master">
    <img src="https://coveralls.io/repos/github/MaxHalford/Prince/badge.svg?branch=master&style=flat-square" alt="Coverage Status"/>
  </a>
  <a href="https://www.codacy.com/app/maxhalford25/Prince?utm_source=github.com&utm_medium=referral&utm_content=MaxHalford/Prince&utm_campaign=Badge_Grade">
    <img src="https://api.codacy.com/project/badge/Grade/d58aa963d6fa425b97d2b9364aecbba1?style=flat-square" alt="Codacy Badge"/>
  </a>
  <a href="https://requires.io/github/MaxHalford/Prince/requirements/?branch=master">
    <img src="https://requires.io/github/MaxHalford/Prince/requirements.svg?branch=master&style=flat-square" alt="Requirements Status"/>
  </a>
</div>

<br/>

<br/>
<div align="center">Prince is a factor analysis library for datasets that fit in memory.</div>
<br/>


## Quick start

Prince uses [pandas](http://pandas.pydata.org/) to manipulate dataframes, as such it expects an initial dataframe to work with. In the following example, a [Principal Component Analysis (PCA)](https://www.wikiwand.com/en/Principal_component_analysis) is applied to the iris dataset. Under the hood Prince decomposes the dataframe into two eigenvector matrices and one eigenvalue array thanks to a [Singular Value Decomposition (SVD)](https://www.wikiwand.com/en/Singular_value_decomposition). The eigenvectors can then be used to project the initial dataset onto lower dimensions.

```python
import matplotlib.pyplot as plt
import pandas as pd

import prince


df = pd.read_csv('data/iris.csv')

pca = prince.PCA(df, n_components=4)

fig1, ax1 = pca.plot_cumulative_inertia()
fig2, ax2 = pca.plot_rows(color_by='class', ellipse_fill=True)

plt.show()
```

The first plot displays the rows in the initial dataset projected on to the two first right eigenvectors (the obtained projections are called principal coordinates). The ellipses are 90% confidence intervals.

![row_principal coordinates](docs/_static/pca_row_principal_coordinates.png)

The second plot displays the cumulative contributions of each eigenvector (by looking at the corresponding eigenvalues). In this case the total contribution is above 95% while only considering the two first eigenvectors.

![cumulative_inertia](docs/_static/pca_cumulative_inertia.png)


## Installation

Although it isn't a requirement, using [Anaconda](https://www.continuum.io/downloads) is a good idea in general for doing data science in Python.

**Via PyPI**

```sh
$ pip install prince
```

**Via GitHub for the latest development version**

```sh
$ pip install git+https://github.com/MaxHalford/Prince
```

Prince has the following dependencies:

- [pandas](http://pandas.pydata.org/) for manipulating dataframes
- [matplotlib](http://matplotlib.org/) as a default plotting backend
- [fbpca](http://fbpca.readthedocs.org/en/latest/), [Facebook's randomized SVD implementation](https://research.facebook.com/blog/fast-randomized-svd/)


## Documentation

Please check out the [documentation](http://prince.readthedocs.io) for a list of available methods.


## License

<a href="https://opensource.org/licenses/MIT">
<img src="http://img.shields.io/:license-mit-ff69b4.svg?style=flat-square" alt="mit"/>
</a>
