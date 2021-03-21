---
title: phylo2L function
categories: [Research,R,phylogeny function]
tags: [phylogeny,phylo class,L table,DDD package,pruneL,phylo2L]
date: 2018-10-24

---

I guess this function is specially useful to [our group](https://www.rug.nl/staff/r.s.etienne/) in which we play with L table. 

L table is an alternative way to a phylo class for phylogenetic information storage. The function `L2phylo` has been implemented in the [DDD package](https://cran.r-project.org/web/packages/DDD/index.html) that converts an L table to a phylo class. This function `phylo2L` does the conversion the other way around. Thus, if you want to apply your model to an empirical data. This may be useful to you.

<!--more-->

`phylo2L` function can be found [here](https://github.com/xl0418/Code/blob/99133e6e5744be7382c038edc5701cd494d8e76c/Pro2/R_p2/phylo2L.R) if you want to improve the function. I have verified it by examining if 

```R  
L=phylo2L(L2phylo(L))
```

Notice that `phylo2L` doesn't have the argument `dropextinct` as what `L2phylo` has. Because to my perspective L table should be consistent with the given phylo class. But if you have a full tree on hand and want to prune it, you can do it like this

```R 
prune_phylo = L2phylo(phylo2L(full tree), dropextinct = TRUE)
prune_L = phylo2L(prune_phylo)
```

Or you can use [`pruneL`](https://github.com/xl0418/Code/blob/f4dfd4acc15af6855572fb4659f396cea14bb83b/Pro2/R_p2/pruneL.R) function that I have developed to prune an L table. More details on `pruneL` function can be found in this [post](https://xl0418.github.io/2018/10/24/2018-10-24-pruneLfunction/).