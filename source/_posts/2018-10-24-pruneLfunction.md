---
title: pruneL function
categories: [Research,R,phylogeny function]
tags: [phylogeny,phylo class,L table,DDD package,pruneL,phylo2L]
date: 2018-10-24

---

I guess this function is specially useful to [our group](https://www.rug.nl/staff/r.s.etienne/) in which we play with L table. But might be less useful than `phylo2L` function :-)

Following last post, this function `pruneL` prunes an L table by removing the extinct lineages.

<!--more-->

`pruneL` function can be found [here](https://github.com/xl0418/Code/blob/f4dfd4acc15af6855572fb4659f396cea14bb83b/Pro2/R_p2/pruneL.R) if you want to improve the function. There is a huge room for improvement. This version is only the first draft of the function. And I guess I should remove the argument `dropextinct`. It doesn't make any sense. What do you think?