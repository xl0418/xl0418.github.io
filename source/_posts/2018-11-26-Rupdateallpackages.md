---
title: R update all packages
categories: [Research, R]
tags: [R,update, packages]
date: 2018-11-26

---

A convenient way to update all the packages.

<!--more-->

## Update all the packages
Very simple, just one piece of code as follows:

```R
update.packages(ask = FALSE, dependencies = c('Suggests'))
```

Run it in the console of your Rstudio and take a cup of coffee. 