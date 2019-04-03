---
output: github_document
---

There is only one slide deck:

  - [Review and devtools](00-usethis.html), for everyone

## usethis

The we are going to use the “usethis” package to help us configure our git and GitHub setup.

There’s a lot of things in package-development (and in project workflows) that end up being rote and repetitive, but painful if it gets messed-up. This is the motivation behind the usethis package.

This is applicable to a lot of things with Tidyverse and r-lib; if it seems like there should be an easier way to do something, there probably is; it should not surprise us to find a function in usethis to help us.

The usethis function is getting *very* close to a CRAN release; it might be released by the time the Unconf starts. In the meantime, we are going to use the development version from GitHub. Because some of the details may change as they put the finising touches on this version, you might see something slightly different from what I see. No worries, the essentials should be the same, and you can always install the latest GitHub version:

```r
devtools::install_github("r-lib/usethis")
```

You may wish to load the package for the next few steps:

```r
library("usethis")
```

### How can I find out about my git and GitHub setup?

Well, there’s a function

```r
git_sitrep()
```

```
* Name: <unset>
* Email: <unset>
* Default protocol: <unset>
* Vaccinated: FALSE
git2r
* Supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
No personal access token found
```

```r
use_git_config(user.name = "Ian Lyttle", user.email = "ian.lyttle@schneider-electric.com")
```

```
User
* Name: 'Ian Lyttle'
* Email: 'ian.lyttle@schneider-electric.com'
* Default protocol: <unset>
* Vaccinated: FALSE
git2r
* Supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
No personal access token found
```

TODO: see if this is a "thing" on RStudio Cloud

```
> use_git_config(user.name = "Ian Lyttle", user.email = "ian.lyttle@schneider-electric.com")
Error in names(old) <- names(values) : 
  attempt to set an attribute on NULL
``` 

```r
browse_github_pat()
```

```r
edit_r_environ()
```

---

Extra

```
edit_r_profile()
```