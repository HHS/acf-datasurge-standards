# R Style Guidelines
The ACF Data Surge team's R Style Guidelines are intended to make our R code consistent and easy to read across projects. Our guidelines align with the [The tidyverse style guide](https://style.tidyverse.org/) and we adopt the [Google R Style Guide](https://google.github.io/styleguide/Rguide.html) approach of listing the ways that our guidelines differ from the tidyverse guidelines. 

Our guidelines are unique in that we include a section at the end detailing preferred packages and package management standards.

## Functions

### Returning Values

- Use return() explicitly for returning values from a function
```
my_mean <- function(x) {
    x_mean <- mean(x)
    return(x_mean)
}
```

## Pipes

### Assignment
- Use only left-hand assignment
```
iris <- iris %>%
    arrange(value)

iris <-
    iris %>%
    arrange(value)
```

## Packages

### Package Management
We will use [renv](https://rstudio.github.io/renv/articles/renv.html) to manage packages for our projects/code written in R. When beginning a new project, create a dedicated R project. This R project, and attendant renv related files, should be tracked on GitHub so that all contributors are working in the same development environment. See the [renv documentation](https://rstudio.github.io/renv/articles/renv.html) for a list of files that should be tracked in Git. Be sure to also include the .Rproj file for the project.

In addition to installing the packages needed for your work, [styler](https://styler.r-lib.org/) and [lintr](https://github.com/r-lib/lintr) should be among the first two things you install. These packages will help make sure that code is conforming to the Tidyverse standards, taking some of the burden of remembering these things off of programmers.

### Preferred Packages

- Data Cleaning: [tidyverse](https://www.tidyverse.org/), [dplyr](https://dplyr.tidyverse.org/), [tidyr](https://tidyr.tidyverse.org/), [arrow](https://arrow.apache.org/docs/r/), [dtplyr](https://dtplyr.tidyverse.org/), [janitor](https://www.rdocumentation.org/packages/janitor/versions/2.2.0)
    - Installing the tidyverse will install both dplyr and tidyr, as well as many other useful packages. However, we encourage parsimony. That is, if only a few of the packages in the tidyverse are needed, do not load them all. This helps with reproducibility, making clear what packages are needed for a specific script, and with performance. To that end we listed packages in the tidyverse individually throughout this guide.
    - When working with large data, prefer arrow and dtplyr to packages such as data.table. The former provide syntax that is similar to the syntax of dplyr without sacrificing much speed.
- Assertive Programming: [assertr](https://www.rdocumentation.org/packages/assertr/versions/3.0.1)
    - Use a combination of base R (e.g. `stop()`, `stopifnot()`) and assertr for assertive programming. In pipelines, prefer assertr.
- Loops: [purrr](https://purrr.tidyverse.org/), [furrr](https://furrr.futureverse.org/)
    - It is acceptable to use the base R `*apply()` suite of functions for looping.
    - Use furrr as a drop-in replacement for purrr if attempting to parallelize code.
- [Quarto](https://quarto.org/): [rmarkdown](https://www.rdocumentation.org/packages/rmarkdown/versions/2.25)
- Reading Data: [readr](https://readr.tidyverse.org/), [readxl](https://readxl.tidyverse.org/), [openxlsx](https://ycphs.github.io/openxlsx/articles/Introduction.html)
    - It is acceptable to use Base R where possible, but we recommend considering readr for its speed and consistent naming conventions.
- Machine Learning/Statistics: [tidymodels](https://www.tidymodels.org/)
- Geospatial Analyses: [sf](https://r-spatial.github.io/sf/), [terra](https://github.com/rspatial/terra)
- String Manipulation: [stringr](https://stringr.tidyverse.org/)
- Visualization: [ggplot2](https://ggplot2.tidyverse.org/), [plotly](https://plotly.com/r/)
- Dashboards: [shiny](https://www.rstudio.com/products/shiny/)