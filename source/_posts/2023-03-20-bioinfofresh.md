---
title: "The first week of getting into the realm of bioinformatics"
categories: [Research, bioinformatics]
tags: [sh]
date: 2023-03-20
mathjax:
  conversion:
    em: 14
  tex:
    tags: 'ams'
  svg:
    exFactor: 0.03
---

The simple workflow of the empirical part of my current project is:

1. Compare the ASVs of the sampled bacteria with data bases to match and obtian possible species identification;

2. From the matched genome ids, fetch the full genome data from GenBank and other sources;

3. Annotate genome using "WHATEVER" programs. Sorry Xin, this word is so impressive to me;

4. Feed the annotated genes to `gRodon` to estimate the maximum growth rates of these bacteria.

Looks quite easy!

CLICK THE TITLE TO SEE MORE PAIN!

<!--more-->

For a newbie to bioinformatics, I summerized these information from the first meeting with [Jesse](https://jcmcnch.github.io/). I was happy that this sounds straightforward if "easy" is not appropriate. OK, develop a pipeline and get things work through automatically. 

# Step 1

The comparison has been done by Jesse (thanks!). A tsv file is generated, recording the species labels and the possible genome ids. So, I only need to download the full genome data by using this genome id. 

# Step 2

It seems that there are many ways to do that. 

* GTDB (Genome Taxonomy Database) has developed a tool [GTDBtk](https://github.com/Ecogenomics/GTDBTk) to make it feasible. **Failed!** Some third-party dependencies are not installable on MacOS M2 chip.  

* Python pkg Entrez. **Failed!** For some reason, `esearch` doesn't work! I even tried to invoke the terminal to run `esearch` from Python. It just got stuck there forever. Meanwhile, even it works in terminal, I've no idea the corresponding database name and `elink --name` for a given genome id. Without that, the file you downloaded is of size 0. 

* R pkg [Biomartr](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5408848/). **Failed!** This is so close to get work done. I managed to download the full genome in Fasta format from the NCBI RefSeq data base. However, due to unkown reason, the summary txt for GenBank cannot be downloaded. Thus, all the matches in GenBank cannot be pulled down. 

* `sh` script adapted from GTDB. **Failed!** The fetch command is like this 

```
!wget -q https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/003/947/435/GCF_003947435.1_ASM394743v1/GCF_003947435.1_ASM394743v1_genomic.fna.gz -O /tmp/gtdbtk/genomes/genome_a.fna.gz
```

However, I only know GCF_003947435.1 this id, not the assembly accession id, i.e. ASM394743v1. Where can I match these two? Give up after a few hours' exploration.

* `sh` using NCBI new tool [datasets](https://www.ncbi.nlm.nih.gov/datasets/docs/v2/how-tos/genomes/download-genome/). Finally, I managed to incorporate this tool in `sh` script and automate the downloading process. Code can be found [**here**](https://github.com/xl0418/GetGenome).

I was happy to see things move on before I realized that I need to download >1 million genome data!

One genome data has size around 400 kb BEFORE unziping. In total, 400 GB or more is needed on local without considering the time cost!

So, in this step, parallelizing this process is a must-do thing. 

# Step 3

When I asked Xin how to annotate genome, she told me that use "whatever" program, just getting a fna file. Emmm, sounds pretty easy. There must be many mature tools across a variety of platforms that allow you to just click-and-wait for annotations done. NOOOO! Do you know how to Docker images? Do you know what to do when installing packages from the default channels and got error message? Do you have >200 GB spare space? Do you know whether the develped packages are compatible with your operation systems? In the end, annotating >1 million genomes locally is the last feather. 

# Step 4

Not get here yet. I only wish `gRodon` is more friendly to me. 

# In the end

This is just a post to remind me of these experience. In fact, it was a lot of fun to dive into data processing and analysis. It also implies that there is still lots of work to do in bioinformatics that make life easier. 

Great thanks to Jesse, Emily, Xin and Lee for their shared information and experience in this field! I apprieciate this oppotunity that enriches my skills and knowledge! 

## The end of the end

Anyone knows how to efficiently and conveniently fetch and annotate genome data? 

How about parallelize `sh` script for a `for` loop?