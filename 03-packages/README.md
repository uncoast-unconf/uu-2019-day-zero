# Packages

This part of the course helps you get started to create packages; the material is contained in the [slides]](package-development.html).

## Requirements

We assume you gone through the [day-zero prep](../00-preparation/README.md):

- installed packages **devtools** and **usethis** (CRAN)

- git installed and configured

- GitHub account, `GITHUB_PAT` set in `.Renviron`
  
- functionality of the [starter `.Rprofile`](https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a)
  
You will also need the **forcats** and  **pkgdown** packages:

```r
install.packages(c("pkgdown", "forcats"))
```

## References

- R Packages book, Hadley Wickham
  - [first edition](http://r-pkgs.had.co.nz/)
  - [second edition](https://r-pkgs.org/) (dev), with Jenny Bryan
  
- [usethis](https://usethis.r-lib.org/) package, Jenny Bryan and Hadley Wickham

- [Packages](https://github.com/hfrick/presentations/blob/master/2019-03-12_package_building/2019-03-12_package_building.pdf), Hannah Frick
  
- [goodPractice](https://github.com/hfrick/presentations/blob/master/2018-06-27_goodpractice/2018-06-27_goodpractice.pdf), Hannah Frick

- [You can make a package in 20 minutes](https://www.rstudio.com/resources/videos/you-can-make-a-package-in-20-minutes/), Jim Hester

