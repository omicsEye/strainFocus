# strainFocus #

**strainFocus** is a workflow to identify strains of bacteria present in metagenomic samples; it is designed to present visualizations to the user that facilitate the interpretation of evolutionary relationships between strains of bacteria found in their samples and among publicly available genomes of the same species.

To run strainFocus, we first run Kneaddata(Lloyd-Price et al., 2019), a quality control software, on the raw reads, generating trimmed reads that are cleaned of contamination. To map the cleaned reads to reference genomes we run HUMAnN(Franzosa et al., 2018) against the uniref90 database. We subsequently use StrainPhlAn(Truong et al., 2017) to concatenate species marker genes present in the samples. We use a script to fetch all other publicly available genomes of interest and then compare the nucleotide similarity of both sample genomes and fetched genomes using RAxML and calculating best fit and parsimony trees. We run StrainPhlAn with the optional arguments --marker_in_n_samples 20 and --sample_with_n_markers 5 to balance a conservative inclusion criteria with a desire to include as many samples as possible in our downstream phylogenetic analyses. The multiple sequence alignment (MSA) files are used to do further downstream analysis and compare strains. 

---

# Citation: #
 Xinyang Zhang, Tyson Dawson, Keith A. Crandall, Ali Rahnavard (2022+), **strainFocus: Phylogenetic Analysis of Pooled Bacterial Genomes to Identify Evolutionary Patterns Among Strains**, https://github.com/omicsEye/strainFocus

# Attention # 
----

Please check our [omicsEye Support Forum](https://forum.omicsEye.org) for common questions before open issue thread there.

----

# strainFocus user manual

## Contents ##
* [Features](#features)
* [strainFocus](#strainFocus)
    * [strainFocus approach](#strainFocus-approach)
    * [Installation](#installation)
      * [Windows Linux Mac](#Windows-Linux-Mac)
      * [Apple M1 MAC](#apple-m1-mac)
* [Getting Started with strainFocus](#getting-started-with-strainFocus)
    * [Test strainFocus](#test-omeClust)
    * [Options](#options) 
    * [Input](#input)
    * [Output](#output)
    * [Demo](#demo)
* [Tutorials for normalized mutual information calculation](#tutorials-for-normalized-mutual-information-calculation)
* [Applications](#applications)
  * [Coronaviruses](#coronaviruses)
* [Support](#Support)
------------------------------------------------------------------------------------------------------------------------------
# Features #
1. Generic metagenomics software that can handle paired or unpaired transcriptomic or metagenomic reads
2. Quality control built-in
3. User-friendly
4. Handles host reads
5. Multiple outputs for further downstream analysis
# strainFocus #
## strainFocus approach ##
<img src="/StrainFocusOverview-01.png" width="400">
## INSTALLATION ##

```commandline
python -m pip install git+https://github.com/omicsEye/strainFocus
```

------------------------------------------------------------------------------------------------------------------------------

# Getting Started with strainFocus #

## Test strainFocus ##

To test if strainFocus is installed correctly, you may run the following command in the terminal:

```#!cmd
strainFocus -h
```
Which yields strainFocus command line options.
```commandline
usage: strainFocus -h 
--seqfile SEQFILE --seqtype SEQTYPE --meta_data META_DATA --metavar METAVAR --anatype {reg,cl} [--fraction FRACTION]

optional arguments:
  -h, --help            show this help message and exit
  --seqfile SEQFILE, -sf SEQFILE
                        files contains the sequences
  --seqtype SEQTYPE, -st SEQTYPE
                        type of sequence: nuc, amino-acid
  --meta_data META_DATA, -md META_DATA
                        files contains the meta data
  --metavar METAVAR, -mv METAVAR
                        name of the meta var (response variable). This is teh lable will be used as phenotype of interest to find genotypes related to it.
  --anatype {reg,cl}, -a {reg,cl}
                        type of analysis
  --fraction FRACTION, -fr FRACTION
                        fraction of main data to run
```


## Options ##

```
$ strainFocus -h
```
## Input ##
1. `--seqfile` or `-sf` PATH to a sequence data file
2. `--seqtype` or `-st` sequence type, values are `amino-acid` and `nu` for nucleotides
3. `--meta_data` or `-md` PATH to metadata file
4. `--metavar` or `-mv` name of the meta variable
5. `--anatype` or `-a` analysis type, options are `reg` for regression and `cl` for classification
6. `--fraction` or `-fr` fraction of the main data (sequence positions) to run. it is optional, 
but you can enter a value between 0 and 1 to sample from the main data set.
## Output ##  
1. correlated positions. We group all the collinear positions together.
2. models summary. list of models and their performance metrics.
3. plot of the feature importance of the top models in *modelName_dpi.png* format.
4. csv files of feature importance based on top models containing, feature, importance, relative importance, 
group of the position (we group all the collinear positions together)
5. plots and csv file of average of feature importance of top models.
6. box plot (regression) or stacked bar plot (classification) for top positions of each model.

## Demo ##
The detailed options will come soon!!!
```commandline
strainFocus --input myReads1.fastq --output strainFocus_demo_output
```

# Support #

* Please submit your questions or issues with the software at [Issues tracker](https://github.com/omicsEye/strainFocus/issues).
