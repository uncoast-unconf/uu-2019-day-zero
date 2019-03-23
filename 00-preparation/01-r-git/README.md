# R and git

Our goal is for everyone's computer to have a "sufficiently-current" version of R and access to git.

Accordingly, we are encouraging folks to have a version of R >= 3.4, and to have git accessible from the command-line.

As usual, we refer to Jenny Bryan et al's [Happy Git and GitHub for the useR](https://happygitwithr.com) for both [R installation](https://happygitwithr.com/install-r-rstudio.html) and [git installation](https://happygitwithr.com/install-git.html).

## R

Every so often, you have to update your R installation. Before installing anything try the **Verification** to see if you need to do anything.

The installation itself is, thankfully, "turn-the-crank". Go to [this CRAN page](https://cloud.r-project.org/), then follow the *Download and Install R* link for your OS.

If you change minor versions, e.g. 3.4 -> 3.5, you also have to reinstall all your packages.

This is *my* basic set of packages that then install a bunch of other packages:

```r
install.packages(c("tidyverse", "rmarkdown", "shiny", "devtools"))
```

If I am working on a project, and I don't have a required package installed, the RStudio IDE will tell me, then offer to install it for me. Usually within a few-days, I'm caught-up. There are some techniques out there that try to make this easier; perhaps I am set-in-my-ways such that I don't mind doing this manually. 

### Verification

```r
R.version.string
```

```
[1] "R version 3.5.2 (2018-12-20)"
```

What we want here is that your R version is at least 3.4, but it might be nice if we were all at 3.5.3.

## Git

Good news: (re-)installing git is something we need to do much-more-rarely than re-installing R. Generally, we re-install git when we upgrade our operating system.

Before installing anything, try the **Verification** - if it works, no need to install anything. If you are on macOS, your computer may offer to install "developer command-line tools"; we suggest you accept the offer!

### Windows

If you are on Windows, we recommend you install [Git for Windows](https://git-for-windows.github.io/).

Following [Happy Git's adivce](https://happygitwithr.com/install-git.html#install-git-windows):

> - **NOTE:** When asked about “Adjusting your PATH environment”, make sure to select “Git from the command line and also from 3rd-party software”. Otherwise, we believe it is good to accept the defaults.
> - Note that RStudio for Windows prefers for Git to be installed below `C:/Program Files` and this appears to be the default. This implies, for example, that the Git executable on my Windows system is found at `C:/Program Files/Git/bin/git.exe`. Unless you have specific reasons to otherwise, follow this convention.

### macOS

Again, we follow [Happy Git](https://happygitwithr.com/install-git.html#macos).

The neat thing about asking macOS about our git version is that it will offer to install git for us if it is not installed.

### Verification

From the Terminal pane in your RStudio IDE, type:

```
git --version
```

On macOS, you may get a on offer to install developer command-line tools, take the offer! For our purposes, you need only the Xcode command line tools (**not all of Xcode**).

I get this:

```
git version 2.17.2 (Apple Git-113)
```

On Windows, I get this:

```
git version 2.21.0.windows.1
```

## Slides

Here are links to the slides for this week's topics for [macOS](r-git-macos.html) and [Windows](r-git-windows.html).
