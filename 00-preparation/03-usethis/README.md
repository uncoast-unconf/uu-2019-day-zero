# usethis

This week only one set of slides and one video - this will work identically on mocOS and Windows.

- [slides](00-usethis.html) for this week
This week you'll find out why I have been reminding you to have access to your GitHub credentials.

### References

- [What They Forgot to Teach You About R](https://whattheyforgot.org/index.html) by Jenny Bryan and Jim Hester (under development)
- where you can [check the email-addresses](https://github.com/settings/emails) you have registered with GitHub
- [starter files](https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a) for `.Renviron` and `.Rprofile`

## Configuration with **usethis**

This week, we are going to use the “usethis” package to help us configure our git and GitHub setup. You'll also find out why I have been reminding you to make sure you have access to your GitHub credentials. 

There’s a lot of things in package-development (and in project workflows) that end up being rote and repetitive, but painful if it gets messed-up. This is the motivation behind the usethis package.

This is applicable to a lot of things with Tidyverse and r-lib; if it seems like there should be an easier way to do something, there probably is; it should not surprise us to find a function in usethis to help us.

### Installation

The usethis package has just had a CRAN release (thanks to Jenny Bryan and her coworkers for the excellent timing)! Let's install the CRAN version:

```r
install.packages("usethis")
```

You may wish to load the package for the next few steps:

```r
library("usethis")
```

### Git situation-report

How can I find out about my git and GitHub setup?

Well, there’s a function for that:

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
```

The first thing we look at is the value of **Git user** > **Vaccinated**; we are looking for `TRUE`.

### Git vaccinate

How to I stay safe with git?

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
```

Note that **Vaccinated** is now `TRUE`. Next, have a look at **Git user** > **Name** and **Email**.

### Git configuration

How do I configure my git?

Git and GitHub use your name and email address to keep track of who commits what. Your email has to be an email you have registered with GitHub.

To remind yourself what email-addresses you set at GitHub. `https://github.com/settings/emails`

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
```

Your **Name** and **Email** should now be set.

Next we look for **GitHub** > **Personal access token**.

### Github access & `.Renviron`

How do we make it easy to authenticate to GitHub?

You can ask GitHub to issue you with a personal access-token - treat this like you treat your password.

Before asking for a PAT, we can prepare the ground by opening your `.Renviron` file. One of the reasons we use a `.Renviron` file is so that we have a single known-place we can keep things we want to secure, like credentials. 

If you work with a firewall, this might also be where you keep your proxy settings. 

```r
edit_r_environ()
```

If you already have stuff in your `.Renviron` file, all we are going to do is possibly add to it. You may want to save a backup copy, just in case.

If you don't have a `.Renviron` file (it opens empty), here's a [starter](https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a) you can use.

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
```

Under **GitHub**, we should see that our **Personal access token** is found, and that it has used our PAT to ask GitHub to tell us our **User** and **Name**.

### More configuration with `.Rprofile`

The last bit of configuration we will do is to set the option for **Default usethis protocol**. THe two available choices are `ssh` and `https`. If you are just starting, I'll recommend you use `https`; if you have `ssh` set up, and it works for you, there is no need to switch to `https`.

The place will set this option is the `.Rprofile` file. The `.Renviron` file helps us stay safe; the `.Rprofile` file helps us stay lazy.

We can use `.Rprofile` to set up options and to specify packages that we want to load when we start an interactive R session.

```r
usethis::edit_r_profile()
```

If you already have stuff in your `.Rprofile` file, all we are going to do is possibly add to it. You may want to save a backup copy, just in case.

If you don't have a `.Rprofile` file (it opens empty), here's a [starter](https://gist.github.com/ijlyttle/dee4a89c8528cd4a0a319bb7b8cdd51a) you can use.

The critical thing is to set the option for `usethis.protocol`, but the other stuff can be handy, too.

Once you are done, save `.Rprofile` and restart R. Then:

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
```

Now you are well-and-truly ready for the Unconf!
