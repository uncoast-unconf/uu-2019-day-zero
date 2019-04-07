# usethis

There is only one slide deck:

  - [Review and devtools](00-usethis.html), for everyone

### References

The we are going to use the “usethis” package to help us configure our git and GitHub setup.

There’s a lot of things in package-development (and in project workflows) that end up being rote and repetitive, but painful if it gets messed-up. This is the motivation behind the usethis package.

This is applicable to a lot of things with Tidyverse and r-lib; if it seems like there should be an easier way to do something, there probably is; it should not surprise us to find a function in usethis to help us.

The usethis package has just had a CRAN release (thanks to Jenny Bryan and her coworkers for the excellent timing)! Let's install the CRAN version:

```r
install.packages("usethis")
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
Git user
* Name: <unset>
* Email: <unset>
* Vaccinated: FALSE
usethis + git2r
* Default usethis protocol: <unset>
* git2r supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
* Personal access token: <unset>
Repo
* Path: '/Users/ijlyttle/Documents/git/github/uncoast-unconf/uu-2019-day-zero/.git'
* Local branch -> remote tracking branch: 'master' -> 'upstream/master'
GitHub pull request readiness
* origin: '<no such remote>'
* upstream: uncoast-unconf/uu-2019-day-zero, NA
```

The first thing we look at is the value of **Git user** > **Vaccinated**; we are looking for `TRUE`.

### How to I stay safe with git?

This keeps you from committing stuff to git that can contain credentials.

```r
git_vaccinate()
```

```r
git_sitrep()
```

```
Git user
* Name: <unset>
* Email: <unset>
* Vaccinated: TRUE
usethis + git2r
* Default usethis protocol: <unset>
* git2r supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
* Personal access token: <unset>
Repo
* Path: '/Users/ijlyttle/Documents/git/github/uncoast-unconf/uu-2019-day-zero/.git'
* Local branch -> remote tracking branch: 'master' -> 'upstream/master'
GitHub pull request readiness
* origin: '<no such remote>'
* upstream: uncoast-unconf/uu-2019-day-zero, NA
```

Note that **Vaccinated** is now `TRUE`. Next, have a look at **Git user** > **Name** and **Email**.

### How do I configure my git?

Git and GitHub use your name and email address to keep track of who commits what. Your email has to be an email you have registered with GitHub.

To remind yourself what emails you set at GitHub: `https://github.com/settings/emails`

If you need to set or update these:

```r
use_git_config(user.name = "Ian Lyttle", user.email = "ian.lyttle@schneider-electric.com")
```

```r
git_sitrep()
```

```
Git user
* Name: 'Ian Lyttle'
* Email: 'ian.lyttle@schneider-electric.com'
* Vaccinated: TRUE
usethis + git2r
* Default usethis protocol: <unset>
* git2r supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
* Personal access token: <unset>
Repo
* Path: '/Users/ijlyttle/Documents/git/github/uncoast-unconf/uu-2019-day-zero/.git'
* Local branch -> remote tracking branch: 'master' -> 'upstream/master'
GitHub pull request readiness
* origin: '<no such remote>'
* upstream: uncoast-unconf/uu-2019-day-zero, NA
```

Your **Name** and **Email** should now be set.

Next we look for **GitHub** > **Personal access token**. If `<unset>`, go through the next section.

### How do we make it easy to authenticate to GitHub?

You can ask GitHub to issue you with a personal access-token - treat this like you treat your password.

Before asking for a PAT, we can prepare the ground by opening your `.Renviron` file. One of the reasons we use a `.Renviron` file is so that we have a single known-place we can keep things we want to secure, like credentials. 

If you work with a firewall, this might also be where you keep your proxy settings. 

```r
edit_r_environ()
```

If you already have stuff in your `.Renviron` file, all we are going to do is possibly add to it. You may want to save a backup copy, just in case.

If you don't have a `.Renviron` file (it opens empty), here's a starter you can use:

https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a

The `GITHUB_PAT` you see here will not work, you need to get your own. Luckily, usethis has a function for that:

```r
browse_github_pat()
```

If you like, rename your PAT - you might wish to get one for every device you have that will access your GitHub account; that way, should the device go away, you can delete the PAT for that device.

Generate the PAT, save it to your clipboard, and copy it to your `.Renviron` file. Up to you if you want to surround the PAT in quotes.

Save your `.Renviron` file, restart R.

```r
# we use `usethis::` because we may not have loaded the package 
usethis::git_sitrep() 
```

```
Git user
* Name: 'Ian Lyttle'
* Email: 'ian.lyttle@schneider-electric.com'
* Vaccinated: TRUE
usethis + git2r
* Default usethis protocol: <unset>
* git2r supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
* Personal access token: '<found in env var>'
* User: 'ijlyttle'
* Name: 'Ian Lyttle'
Repo
* Path: '/Users/ijlyttle/Documents/git/github/uncoast-unconf/uu-2019-day-zero/.git'
* Local branch -> remote tracking branch: 'master' -> 'upstream/master'
GitHub pull request readiness
* origin: '<no such remote>'
* upstream: uncoast-unconf/uu-2019-day-zero, can push
```

Under **GitHub**, we should see that our **Personal access token** is found, and that it has used our PAT to ask GitHub to tell us our **User** and **Name**.

At this point, we are ready to start day-zero. If you want to get a little further-ahead, we will set the option for **Default usethis protocol** in a `.Rprofile` file.

## Extra credit

The `.Renviron` file helps us stay safe; the `.Rprofile` file helps us stay lazy.

We can use `.Rprofile` to set up options and to specify packages that we want to load when we start an interactive R session.


```r
usethis::edit_r_profile()
```

If you already have stuff in your `.Rprofile` file, all we are going to do is possibly add to it. You may want to save a backup copy, just in case.

If you don't have a `.Rprofile` file (it opens empty), here's a starter you can use:

https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a


Once you are done, save `.Rprofile` and reastart R. Then:

```r
# if you specified to load `usethis` for interactive sessions
git_sitrep()
```

```
Git user
* Name: 'Ian Lyttle'
* Email: 'ian.lyttle@schneider-electric.com'
* Vaccinated: TRUE
usethis + git2r
* Default usethis protocol: 'https'
* git2r supports SSH: TRUE
* Credentials: '<usethis + git2r default behaviour>'
GitHub
* Personal access token: '<found in env var>'
* User: 'ijlyttle'
* Name: 'Ian Lyttle'
Repo
* Path: '/Users/ijlyttle/Documents/git/github/uncoast-unconf/uu-2019-day-zero/.git'
* Local branch -> remote tracking branch: 'master' -> 'upstream/master'
GitHub pull request readiness
* origin: '<no such remote>'
* upstream: uncoast-unconf/uu-2019-day-zero, can push
```

Now you are well-and-truly ready for the Unconf!
