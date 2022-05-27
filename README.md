# cMAGfilter
Filtering faulty circularized genome using conspecific MAGs.

### Workflow introduction
Reconstruction of the circularized genomes is the ultimate goal of prokaryotic genome assembly. The development of accurate long-read sequencing technology enables the assembly of circularized genomes from highly complex metagenomic samples. However, prokaryotic genomes tend to have many repetitive sequences, and those often result in faulty assembly closing, thereby generating circularized genomes with significant gaps. cMAGfilter filters out the circularized metagenome-assembled genomes (cMAGs) with such gaps using their conspecific MAGs. For a given cMAG and its conspecific MAGs, it first searches core contigs, the contigs shared by most of the conspecific MAGs, from conspecific MAGs. Next, it calculates the core contig retrieval rate from the cMAG and filters out the cMAG using the information.

![](images/introductory.png)

### Requirements
cMAGfilter requires Python>=3.6 and [mummer4](https://mummer4.github.io/) package.
You can install mummer from its [tarball](https://github.com/mummer4/mummer/releases) or from [bioconda](https://bioconda.github.io/recipes/mummer4/README.html?highlight=mummer4#package-package%20&#x27;mummer4&#x27;).
Please locate the mummer4 package softwares in PATH or specify the location with -nuc parameter.

### Setting up cMAGfilter
`git clone https://github.com/netbiolab/cMAGfilter.git`<br />
`cd cMAGfilter`<br />
`python3 setup.py install --user`

### Testrun with example input data
`python3 cMAGfilter.py examples/input/circular_contigs/Akkermansia_muciniphila.fna examples/input/conspecific_MAGs/Akkermansia_muciniphila examples/output/Akkermansia_muciniphila`

### Output data and the format
You can find the example output files from 'examples/output/Mesosutterella_multiformis'.
- all_by_all_alignment_results/ : This directory contains all-by-all nucmer alignment results between conspecific MAGs.
- Mesosutterella_multiformis_align_back_results/: This directory contains core contigs to circular contig nucmer alignment results.
- conspecific_genomes.contig_report.tsv: This file contains the information on whether the contigs of a conspecific MAG are founded from the other conspecific MAGs.
- Mesosutterella_multiformis_core_contigs_alignment.core_contig_stat.tsv: 
- core_contigs.fna: FASTA file for core contigs
- Mesosutterella_multiformis_core_contigs_alignment.summary.tsv:

### Publication dataset
The entire 110 HiFi circular contigs and thir conspecific MAGs used in the paper are available from the [link](http://netbiolab.org/wiki/pubfiles/HiFi_publication_dataset.tar.gz) (6.6GB).

### Citation
CY Kim, J Ma, I Lee, [HiFi Metagenomic Sequencing Enables Assembly of Accurate and Complete Genomes from Human Gut Microbiota](https://www.biorxiv.org/content/10.1101/2022.02.09.479829v1), bioRxiv preprint, Feb. 2022
