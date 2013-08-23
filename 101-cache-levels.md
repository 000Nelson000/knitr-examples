# Different cache levels

`cache=FALSE` or `cache=0` means no cache:


```r
Sys.sleep(1)
1 + 1
```

```
## [1] 2
```

```r
plot(cars)
```

![plot of chunk test-a](http://animation.r-forge.r-project.org/knitr-ex/figure/101-cache-levels-test-a.png) 


`cache=1` means to save the results from `evaluate::evaluate()`, and pretend
the code has been evaluated; all the output hooks will be applied every time
the document is recompiled; note the plots are also saved as display lists,
and will be redrawn every time the document is recompiled:


```r
Sys.sleep(1)
1 + 1
```

```
## [1] 2
```

```r
plot(cars)
```

![plot of chunk test-b](http://animation.r-forge.r-project.org/knitr-ex/figure/101-cache-levels-test-b.png) 


`cache=2` is similar to `cache=1`, and the only difference is that the plots
will not be redrawn, in which case you need to make sure you did not delete
the figure files manually;


```r
Sys.sleep(1)
1 + 1
```

```
## [1] 2
```

```r
plot(cars)
```

![plot of chunk test-c](http://animation.r-forge.r-project.org/knitr-ex/figure/101-cache-levels-test-c.png) 


`cache=TRUE` or `cache=3` means to cache the text output of a chunk; none of
the output hooks will be called when the document is recompiled, and the
plots will not be redrawn, either:


```r
Sys.sleep(1)
1 + 1
```

```
## [1] 2
```

```r
plot(cars)
```

![plot of chunk test-d](http://animation.r-forge.r-project.org/knitr-ex/figure/101-cache-levels-test-d.png) 


Below is a test case for [#588](https://github.com/yihui/knitr/issues/588):


```r
pairs(matrix(rnorm(100), ncol = 100), labels = 1:100, pch = ".")
```

![plot of chunk test-e](http://animation.r-forge.r-project.org/knitr-ex/figure/101-cache-levels-test-e.png) 

