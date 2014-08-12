[![DOI](https://zenodo.org/badge/doi/10.5281/zenodo.11266.png)](http://dx.doi.org/10.5281/zenodo.11266)

This page describes the R package decompr.

## Installation
The package is currently not on cran but can be downloading using the `devtools` package.

{% highlight r linenos %}
# install.packages('devtools')
devtools::install_github('bquast/decompr')
{% endhighlight %}

## Usage
The usage is described in the R documentation included in the package. In addition...

{% highlight r linenos %}
# load the package
library(decompr)

# load World Input-Output Database for 2011
data(wiod)

# explore the data
dim(intermediate.demand) # (2 + GN + totals) x (2 + GN)
dim(final.demand)        # (2 + GN + totals) x (2 + G*5)
intermediate.demand[1:40,1:40]
final.demand[1:40,1:10]

# use the direct approach
# run the WWZ decomposition
wwz <- decomp(intermediate.demand, final.demand, method='wwz')
wwz[1:5,1:5]

# run the Kung Fu decomposition
kf  <- decomp(intermediate.demand, final.demand, method='kung.fu')
kf[1:5,1:5]

# or use the step-by-step approach
# create intermediate object (class decompr)
decompr.object <- load.tables(intermediate.demand, final.demand)
str(decompr.object)

# run the WWZ decomposition on the decompr object
wwz <- wwz(decompr.object)
wwz[1:5,1:5]

# run the Kung Fu decomposition on the decompr object
kf  <- kung.fu(decompr.object)
kf[1:5,1:5]
{% endhighlight %}

## Contribute
The development version is available on Github, in fact this page is a branch of the **decompr** repository. The repository can be found at https://github.com/bquast/decompr.


## About the page

This page is hosted on Github pages, render using jekyll and uses the Solo theme by
Shu Uesugi.