# strainFocus: #

**strainFocus** is a workflow to identify strains of bacteria present in metagenomic samples; it is designed to present visualizations to the user that facilitate the interpretation of evolutionary relationships between strains of bacteria found in their samples and among publicly available genomes of the same species.

To run strainFocus, we first run Kneaddata(Lloyd-Price et al., 2019), a quality control software, on the raw reads, generating trimmed reads that are cleaned of contamination. To map the cleaned reads to reference genomes we run HUMAnN(Franzosa et al., 2018) against the uniref90 database. We subsequently use StrainPhlAn(Truong et al., 2017) to concatenate species marker genes present in the samples. We use a script to fetch all other publicly available genomes of interest and then compare the nucleotide similarity of both sample genomes and fetched genomes using RAxML and calculating best fit and parsimony trees. We run StrainPhlAn with the optional arguments --marker_in_n_samples 20 and --sample_with_n_markers 5 to balance a conservative inclusion criteria with a desire to include as many samples as possible in our downstream phylogenetic analyses. The multiple sequence alignment (MSA) files are used to do further downstream analysis and compare strains. 

---

# Citation: #
 Xinyang Zhang, Tyson Dawson, Keith A. Crandall, Ali Rahnavard (2022+), **strainFocus: Phylogenetic Analysis of Pooled Bacterial Genomes to Identify Evolutionary Patterns Among Strains**, https://github.com/omicsEye/strainFocus

# Attention # 
----

Please check our [omicsEye Support Forum](https://forum.omicsEye.org) for common questions before open issue thread there.

----
