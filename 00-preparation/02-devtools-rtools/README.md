# devtools

[Slides](00-review-devtools.html)

---

## Review

### References

- [Happy Git](https://happygitwithr.com/) by Jenny Bryan et al.

### Week 0

- RStudio (version 1.2)
- Github account, you have access to credentials, you can say hello in a couple of places - to [introduce yourself](https://github.com/uncoast-unconf/uu-2019-day-zero/issues/11), and to let us know about what you think of [your role at the Unconf](https://github.com/uncoast-unconf/uu-2019/issues/17)
  - if you have any problems, I go too fast, etc. Here's [another place](https://github.com/uncoast-unconf/uu-2019-day-zero/issues/12) to get help. Or email me.
  
  
### Week 1  
  
- git: using Terminal, this returns something sensible

```
git --version
```

- R: version > 3.4

```r
R.version.string
```

## devtools

For building and working with packages, the [devtools](https://devtools.r-lib.org/) package makes our lives a lot easier; these are the tools that the Tidyverse team use themselves.

Our main task this week: 

```r
install.packages("devtools")
````

On Windows, if you get a warning about Rtools not installed, ignore it *for now*.

To confirm everthing is working:

```r
devtools::has_devel(debug = TRUE)
```

On Windows, if you do not have Rtools installed, devtools will offer to install it for you. I urge you to accept the offer.

Once Rtools has finished installing, try `devtools::has_devel(debug = TRUE)` again.

Next, we will install a package from GitHub using devtools:

```r
devtools::install_github("r-lib/usethis", force = TRUE)
```

If these return without error, **you're done** for the week.

