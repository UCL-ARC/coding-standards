# R recommendations

## Tidyverse style guide

In general, we recommend following the [Tidyverse style guide](https://style.tidyverse.org/) as much
as possible. There are two R packages that support this style guide out of the box:

* [*styler*](http://styler.r-lib.org/) allows interactively styling selected text, files or entire projects.
  It includes a handy RStudio plugin to make your R code beautiful with one simple keyboard shortcut
* [*lintr*](https://github.com/jimhester/lintr) checks whether your code conforms to the style guide and flags
  potential problems. It can also be enabled in RStudio.

Both these tools can be customised to disable certain checks or using different values. However, we
recommend sticking to the default values as much as possible.

For VSCode users, the [vscode-R](https://code.visualstudio.com/docs/languages/r) plugin provides most
of these features in VSCode as well.

> A note on the use of the pipe (`|>` or `%>%`) operator, although
>[very useful for data analysis code](https://r4ds.hadley.nz/workflow-style.html#sec-pipes), 
>we recommend to avoid their usage in **R package code**. The main reason is that pipes make code 
>more difficult to debug, especially for very long sequences of pipes, as the intermediate objects
>are not immediately accessible. In addition, the use of `%>%` would incur an additional dependency.

## Package development

The [*R Packages*](https://r-pkgs.org/) book provides a comprehensive guide to R package development,
which closely follows the *Tidyverse style guide* (as they're from the same authors). We recommend
following the best practices described in this book.

To help with adhering to these practices and make your life as an R developer much easier, there are
the [*devtools*](https://devtools.r-lib.org/) and [*usethis*](https://usethis.r-lib.org/) packages.
From setting up your package file structure with `usethis::create_package()`, running unit tests
and other checks with `devtools::check()`, to publishing your package to CRAN with `devtools::release()`,
these two packages have it all covered. In fact, whenever you need to do anything other than edit
an `*.R` file, there is probably a [*usethis* function](https://usethis.r-lib.org/reference/index.html)
function you can (and should!) use instead. And if there is not, ask yourself whether you really need
to do that thing.

And of course, both these packages play nicely together with RStudio, with several built-in features
and shortcuts (see the *R Packages* book for tips and tricks).

## CI with GitHub Actions

The [r-lib/actions](https://github.com/r-lib/actions) repository contains several reusable *GitHub Actions* (GHA)
workfklows for R projects (not only packages). The [examples](https://github.com/r-lib/actions/tree/v2/examples)
directory provides complete workflows for common R project CI tasks. All of these can be easily set up
using [`usethis::use_github_action()`](https://usethis.r-lib.org/reference/use_github_action.html).

## Bioconductor

When developing an R package for the [Bioconductor project](https://bioconductor.org/), a few exceptions
to the above recommendations should be considered. Bioconductor provides
[their own list of recommendations](https://contributions.bioconductor.org/r-code.html). These are
largely similar to the *Tidyverse style guide*, with a few exceptions:

* Use of 4 spaces for indenting instead of 2
* Use of `camelCase` for function names

The reason for the latter is that Bioconductor packages make extensive use of the [S4](https://adv-r.hadley.nz/s4)
OOP framework in R. Within this framework, the convention is to use `CamelCase` for Class names and
`camelCase` for method names.

The most important of these rules are checked by
[`BiocCheck::BiocCheck()`](https://bioconductor.org/packages/release/bioc/html/BiocCheck.html)
The [*biocthis*](https://bioconductor.org/packages/release/bioc/html/biocthis.html) package provides
a handy alternative to *usethis* for Bioconductor packages. Finally, there is a
[bioc-actions](https://github.com/grimbough/bioc-actions) with Bioconductor-specific GHA workflows.

The *biocthis* package provides [`biocthis::bioc_style()`](https://lcolladotor.github.io/biocthis/reference/bioc_style.html)
to configure the *syler* package with the *Bioconductor*-specific rules.
You can set `options(styler.addins_style_transformer = "biocthis::bioc_style()")` in your `~/.Rprofile`
to configure these rules globally, or in a project-specific `.Rprofile`.

