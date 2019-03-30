# devtools and Rtools

There are a couple of slide decks this week:

- [Review and devtools](00-review-devtools.html), for everyone
- [Rtools](01-rtools.html), for Windows only (sorry!)

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

For building and working with packages, the [devtools](https://devtools.r-lib.org/) package makes our lives a lot easier; these are the tools that the Tidyverse teams use themselves.

Our main task this week: 

```r
install.packages("devtools")
````

To confirm everthing is working:

```r
devtools::has_devel(debug = TRUE)
```

```r
devtools::install_github("r-lib/usethis", force = TRUE)
```

If these return without error, **you're done** for the week.

If you are using macOS, this should **just work**.
 
If you are using Windows, you may have to install Rtools (see next section). 

## Rtools

- check the version, Open `C:\Rtools\version.txt`.
- if need be, uninstall the old version

To install a new version of Rtools:

- go to [https://cloud.r-project.org/](https://cloud.r-project.org/) > **Download R for Windows** > **Rtools**
- download `Rtools34.exe`
  - I find that on *my* Windows machine, I have problems using Rtools 3.5. However, everything seems to work well using Rtools 3.4, even though I am running R 3.5.

- set the PATH
  - you can do this during the installation process 
  - make sure PATH starts with `C:\Rtools\bin;`

To confirm:

```r
devtools::has_devel(debug = TRUE)
```

```r
devtools::install_github("r-lib/usethis", force = TRUE)
```

