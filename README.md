# MethBusters
Methylation tools for Long-Read Seq data (e.g. PacBio or ONT)

## Introduction

This repository contains a set of scripts for analysing methylation variation in human/mammalian genomic data. Specifically this workflow can
perform the following:

* Standardizing of haplotyped sets into a 3-bedmethyl .bed file (with imputation of missing calls due to non-phasing)
* Parent-of-origin haplotyping (if external short-read or long-read varaint call data is available for parents)
* Preparation of a background call model (leave-one-out averages and stdev for selected regions, CpG islands, or tiled genomic bins)
* analysis of methylation variation from the background call model
* auxiliary scripts for calling DMI (differentially methylated/imprinted regions), for fast gene-centric annotaion of called regions

Inputs: bedmethyl files (as produced by [PacificBiosciences/pb-CpG-tools|https://github.com/PacificBiosciences/pb-CpG-tools] or [nanoporetech/dorado|https://github.com/nanoporetech/dorado] components, 
or by integrated pipelines: [PacificBiosciences/HiFi-human-WGS-WDL|https://github.com/PacificBiosciences/HiFi-human-WGS-WDL] or [epi2me-labs/wf-human-variation|https://github.com/epi2me-labs/wf-human-variation].

Outputs:
bed files with scores (can be treated as tab-separated files)

## Compute requirements

Minimum requirements:

+ CPUs = 1
+ Memory = 16GB

Approximate run time: less than 1 minute per sample x N_samples to build the background model (METHBGROUND.bed); less than 1 minute per sample to call aberrantly methylated regions.

## Install and run

Compile .c files using make in src/ directory. Copy binaries to your $PATH.
Use binaries and perl scripts on included test datasets (only chr1), or on included precomputed background files for PacBio or ONT.

