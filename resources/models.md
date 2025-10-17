---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.17.3
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---



# Modeling Preliminaries


```{code-cell} ipython3
import pandas as pd
import seaborn as sns
from scipy import stats
import numpy as np
from sklearn.model_selection import train_test_split
from sklearn.naive_bayes import GaussianNB
from sklearn.metrics import confusion_matrix, classification_report, roc_auc_score 
import matplotlib.pyplot as plt

sns.set_theme(palette='colorblind')
```

## Identity matrices 

```{code-cell} ipython3
:label: identitymatrix
D = 4
np.eye(D)
```

```{code-cell} ipython3
:label: diagonalcov
3*np.eye(D)
```

(dist:gaussian)=
## Gaussian Distribution

The Gaussian also known as normal distribution. It can be [univariate](#dist:univariategaussian) or multivariate](#dist:multivariategaussian). In one dimension it is shaped like a [bell curve](#stdnorm) and in two dimensions it is like [hill](#mvn). It has two parameters, the mean that shifts its location([in one dim along the axis](#shiftnorm) or in [either/both directions in two dims](#shiftmvn)) and the scale changes the shape. In one dimenion the scale is the variance and [controls the width](#stretchnorm).  In two dimensions the scale is the covariance matrix, its [diagonal controls the width and height](#stretchmvn) and the [off diagonals control the skew(angle)](#skewmvn)

(dist:univariategaussian)=
### Univariate Gaussian
in one dimension is like:

$$P(x)  = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{x-\mu}{\sigma}\right)^2}$$

where:
- $x$ is the scalar random variable 
- $\sigma^2$ is the variance (the {term}`scale parameter` )
- $\mu$ is the mean (the {term}`location parameter`)

::::{hint}
numpy/scipy/sklearn refer to parameters as `loc` for {term}`location <location parameter>` and `scale` for {term}`scale parameter`  instead of the specific names for individual distributions to create a more uniform api
::::::

```{code-cell} ipython3
:tags: [hide-input]
:label: stdnorm
x = np.linspace(-10, 10, 1000)
var = 1
mu = 0
plt.plot(x, stats.norm.pdf(x, loc=mu, scale=var), 
         label=r'$\mu=0, \sigma=1$', linewidth=2)
plt.title(f'Univariate Gaussian with mean={mu} and var={var} ')
```

The mean parameter changes the location of the distribution

```{code-cell} ipython3
:tags: [hide-input]
:label: shiftnorm
var = 1
mu = 3
plt.plot(x, stats.norm.pdf(x, loc=mu, scale=var), 
         label=r'$\mu=0, \sigma=1$', linewidth=2)
plt.title(f'Univariate Gaussian with mean={mu} and var={var} ')
```

and the scale controls how wide it is. 

```{code-cell} ipython3
:tags: [hide-input]
:label: stretchnorm
var = 3
mu = 0
plt.plot(x, stats.norm.pdf(x, loc=mu, scale=var), 
         label=r'$\mu=0, \sigma=1$', linewidth=2)
plt.title(f'Univariate Gaussian with mean={mu} and var={var} ')
```

(dist:multivariategaussian)=
### Multivariate Gaussian 

For a vector random variable it is written: 

$$P(\mathbf{x}) = \frac{1}{\sqrt{(2\pi)^k|\boldsymbol{\Sigma}|}} \exp\left(-\frac{1}{2}(\mathbf{x}-\boldsymbol{\mu})^T\boldsymbol{\Sigma}^{-1}(\mathbf{x}-\boldsymbol{\mu})\right)$$

where: 
- $\mathbf{x}$ is the vector random variable 
- $\boldsymbol{\Sigma}$ is the covariance matrix
- $\boldsymbol{\mu}$ is the vector mean
- $^T$ is the {term}`transpose` operator

In 2D we can plot the density with a contour plot: 

```{code-cell} ipython3
:tags: [hide-input]
:label: mvn
mu = np.array([0, 0])  # mean vector
cov = np.array([[1, 0],    # covariance matrix
                [0, 1]])

# Create a grid of points
x = np.linspace(-4, 4, 100)
y = np.linspace(-4, 4, 100)
X, Y = np.meshgrid(x, y)

# Stack X and Y to create position array
pos = np.dstack((X, Y))

# Create multivariate normal distribution
mvn = stats.multivariate_normal(mu, cov)

# Evaluate PDF at grid points
Z = mvn.pdf(pos)

# Create contour plot
contours = plt.contour(X, Y, Z, levels=10, colors='blue')
plt.contourf(X, Y, Z, levels=20, alpha=0.6, cmap='Blues')
plt.colorbar(label='Probability Density')
plt.title(f'MVN with mean={mu} and cov={cov} ')
```

The mean still controls the location
```{code-cell} ipython3

mu = np.array([2, 1])  # mean vector
```


```{code-cell} ipython3
:tags: [hide-input]
:label: shiftmvn

# Create multivariate normal distribution
mvn = stats.multivariate_normal(mu, cov)

# Evaluate PDF at grid points
Z = mvn.pdf(pos)

# Create contour plot
contours = plt.contour(X, Y, Z, levels=10, colors='blue')
plt.contourf(X, Y, Z, levels=20, alpha=0.6, cmap='Blues')
plt.colorbar(label='Probability Density')
plt.title(f'MVN with mean={mu} and cov={cov} ')
```


The main diagonal of the covariance control controls the width and height
```{code-cell} ipython3
mu = np.array([0, 0])  # mean vector
cov = np.array([[2, 0],    # covariance matrix
                [0, .5]])
```

```{code-cell} ipython3
:tags: [hide-input]
:label: stretchmvn

# Create multivariate normal distribution
mvn = stats.multivariate_normal(mu, cov)

# Evaluate PDF at grid points
Z = mvn.pdf(pos)

# Create contour plot
contours = plt.contour(X, Y, Z, levels=10, colors='blue')
plt.contourf(X, Y, Z, levels=20, alpha=0.6, cmap='Blues')
plt.colorbar(label='Probability Density')
plt.title(f'MVN with mean={mu} and cov={cov} ')
```


The off diagonal elements of the covariance control controls the angle or skew
```{code-cell} ipython3

mu = np.array([0, 0])  # mean vector
cov = np.array([[2, .7],    # covariance matrix
                [.7, .5]])
```

```{code-cell} ipython3
:tags: [hide-input]
:label: skewmvn

# Create multivariate normal distribution
mvn = stats.multivariate_normal(mu, cov)

# Evaluate PDF at grid points
Z = mvn.pdf(pos)

# Create contour plot
contours = plt.contour(X, Y, Z, levels=10, colors='blue')
plt.contourf(X, Y, Z, levels=20, alpha=0.6, cmap='Blues')
plt.colorbar(label='Probability Density')
plt.title(f'MVN with mean={mu} and cov={cov} ')
```



```{code-cell} ipython3
```
