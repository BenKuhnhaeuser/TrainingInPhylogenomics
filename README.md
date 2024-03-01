# Documentation for training in phylogenomics
 
This repository aims to serve as a starting point for learning how to perform various phylogenomic analyses, especially how to estimate species trees from sequence data.

Some Background for this analysis is given including brief introductions to some computing subjects, links to existing tutorials, including those compiled by people at Kew and useful Linux commands for running programs and analysing the outputs. The focus is on the generation of trees for angiosperm plants (but the methods can be used for other organisms. Hello fungal people.)

If you would like to contribute content to this repository please contact an existing contributor at RGB Kew.

***

## Context
[ Ideas for content topics (very short paragraph on each):
* Why build trees with sequence data?
  * What does it tell you that taxonomy can't?
* Discuss models of evolution and tree building algorithms
  * Discuss Jukes Cantor, Kimura, F84 and REV models; model testing
  * Discuss different types of tree method: distance matrix, parsimony, maximum likelihood and Bayesian analysis - this document discusses macimum likelihood only.
* What sequences are required for the analysis - discuss 
  * requirement for orthologous loci
  * NGS techniques - e.g.'s:
    * RAD-Seq
    * target capture of gene regions
      * mention baits and enrichment  - requirement of short ( e.g 120bp) bait seqs designed against a subset of target genes selected from the genome
      * Various methods but recommend HybPiper (Johnson et al)
      * Requires a bait kit for enrichment and reference target sequences (Angios353)
      * Mention skimming is possible
      * Mention MEGA353 and family-specific kits
* Data mining enables analysis to fit into context of existing data if closely related examples exist: OneKP, SRA, PAFTOL, Earth biogenomes, Darwin, 10KP etc - links to all large projects
* Annotating trees with taxonomy and other data sets
  * WCVP
  * Angiosperms353 - or section on existing tree resources incl Explorer
]
* Preforming the analysis - any online tools for estimating a species tree?

### References
* A recent review paper on phylogenomics
* Johnson et al target capture paper and Angios353 paper

***

## Workflow outline for estimating a species tree
This workflow is discussed briefly in six sections below but consists of two major steps:
* **step 1:** assembly of gene sequences from samples
* **step 2** organising sequences into gene sets, aligning the genes and  using the alignments to estimate a species tree

It is assumed that target capture data is being used and available in the form of Illumina short pair end reads in [fastq format](https://en.wikipedia.org/wiki/FASTQ_format). At the end of this section, there are links to existing more detailed documentation on how to run the programs. Following this section there are some details on computing requirements and a section that summarizes the commands required for a complete analysis.

### Sequencing data quality checks
* Adaptor trimming
* Quality trimming
* Trimmomatic tool
* FASTQC

**_Outputs_**     (and **_Interpretation_**)
* Trimmomatic output - expected % retained pair end and single end reads; single can also be used in HybPiper (can be 7% of total reads).
* 
**_Go further_**
  
### Choice of sample and gene name
Some thought needs to be given to sample and gene names/identifiers before starting the analysis. It is also good to understand how these identifiers are used during the analysis. HybPiper has a novel (?) convention of using the following format for the fasta header in the reference fasta targets file:
```
>SampleName-GeneName
```
with a dash between the sample and gene names. It is best that names should consist of alphanumerical characters only(1 - 9, A -Z, a - z) and underscore characters if required but certainly no dash characters or spaces. It is recommend ...
REWORK THIS
* The sample names should be simple alphanumerical identifiers during the analysis. Meanwhile a mapping file can be prepared to allow the species names to be swapped with the identifier
### 
### Gene recovery from samples
* HybPiper
* Organising sequences into gene sets
* Output DNA sequences should be in frame

**_Outputs_**    (and **_Interpretation_**)

**_Go further_**
* Captus software (?)

### Alignment of genes from samples
Intro - Various easy to use alignment programs exist - recommended ones: MAFFT, UPP for large alignments

**_Outputs_** (and **_Interpretation_**)
* Assessment: AMAS summary
* Filtering tools: AMAS, Trimal
* Removal of long branches with TreeShrink

**_Go further_**
* Concatenation --> species tree (also see two sections below)
* DNA aligned by protein sequence
* Rogue taxon programs

###  Estimating gene trees
Intro:
* Various easy to use maximum likelihood tree programs exist - recommended ones (in order of speed): FastTree, IQTREE, RAxML
    * recommended program options e.g. IQTREE Ultrafastbootstrap
* Virtues of each one: speed, ease of use, documentation

**_Outputs_** (and **_Interpretation_**)
* Newick file format and manipulation of
* Assessment: support values
* Adding taxonomy and visualisation

**_Go further_**

### Estimating the species tree
Intro - choice of program: ASTRAL

**_Outputs_** and **_Interpretation_**
  * Assessment of support values e.g. what do the pp1 scores mean? explain roots - trees are unrooted; Recommended value of confidence = >0.95 (ref)
	Normalised quartet score
  * Visualisation

**_Go further_**

* e.g. concatenation; partitioning data with with RAxL-NG; not as robust a method to ILS as ASTRAL summary method but gives you real branch lengths which might be of interest e.g. long branches that coincide with particular taxonomic levels (or not!) 
* intro to incongruence
* other programs to investigate e.g. ASTRAL-MP, ASTRAL-Pro
* Tanglegrams

### Detailed workflows online
The following links to tutorials go into further details about processing read data and estimating trees. Some additional computing knowledge required and is  discussed in the next section.

* Sidonie's workflow
* Ben's workflow
* PAFTOL Explorer workflow
*   

### References
*** 

## Computing requirements and software
It is very likely that phylogenic analysis will require use of high performance computing due to the hundreds of genes used, unless the number of samples being compared is very small e.g. under 20). Therefore some computing expertise is required     


### Courses

### Linux command line

### Slurm

### Python

### Java

### R

### Installing software

***

## Skeleton workflow summary
This section is a very short summary of the commands required for a complete analysis. It will takes the example data set from HybPiper and  works through read preparation, HybPiper gene recovery, gene alignment with MAFFT, gene tree estimation with IQTREE2 and ASTRAL tree for estimating the species tree

* Suggest to follow HybPiper2 tutorial
* then detail from the gene alignment step
    [yet to outline]


## Contributors
* Paul Bailey
* Sidonie Bellot
* Ben Kuhnhaeuser

## Guide To contributors
* Need to think how the document(s) can be modified. Is it best to transfer agreed tracked changes from e.g. a Google doc?
  * Can edit online and leave a commit message with your name - there's even an extended message box to leave further info
* The idea is the the content should be very succinct and to the point
* Maybe contributors should meet occasionally to assess structure and agree new content
* If the document grows significantly or new topics are included, could break out into several files
* Might be good to relay experiences we have had w.r.t. some statistics, values that might be hard to find from reading tutorials and literature e.;g. maximum expected gene recovery form a sample in base pairs with Angiosperms353 reference targets (±260kbp); guide for amount of cpu and memory to use







---
<span style="font-size:small;">Copyright © 2024 The Board of Trustees of the Royal Botanic Gardens, Kew</span>



