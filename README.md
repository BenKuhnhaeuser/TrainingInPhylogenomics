# Documentation for training in phylogenomics
 
This repository aims to serve as a starting point for learning how perform various phylogenomic analyses, especially how to estimate species trees from sequence data.

Some Background for this analysis is given including brief introductions to some computing subjects, links to existing tutorials, including those compiled by people at Kew and useful Linux commands for running programs and analysing the outputs. The focus is on the generation of trees for angiosperm plants (but the methods can be used for other organisms).

If you would like to contribute content to this repository please contact an existing contributor at RGB Kew.

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
      * Various methods but recommend HybPiper (Johnson et al)
      * Requires a bait kit for enrichment and reference target sequences (Angios353)
      * Mention skimming is possible
      * Mention MEGA353 and family-specific kits
* Annotating trees with taxonomy and other data sets
  * WCVP
  * Angiosperms353 - or section on existing tree resources incl Explorer
]

### Context references
* A recent review paper on phylogenomics
* Johnson et al target capture paper and Angios353 paper

## Workflow outline for estimating a species tree
This workflow is discussed briefly in six sections below but consists of two major steps:
* **step 1:** assembly of gene sequences from samples
* **step 2** organising sequences into gene sets, aligning the genes and  using the alignments to estimate a species tree

It is assumed that target capture data is being used and available in the form of Illumina short pair end reads. At the end of this section, there are links to existing more detailed documentation on how to run the programs. Following this section there a some details on computing requirements and 

### Sequencing data quality checks
* Adaptor trimming
* Quality trimming
* Trimmomatic tool
* FASTQC
  
### Sample and gene idnetifiers
  
### 
### Gene recovery from samples
* HybPiper
* Organising sequences into gene sets

### Alignment of genes from samples
* Various easy to use alignment programs exist - recommended ones: MAFFT, UPP for large alignments
* Assessment: AMAS summary
* Concatenation --> species tree

###  Estimating gene trees
* Various easy to use maximum likelihood tree programs exist - recommended ones (in order of speed): FastTree, IQTREE, RAxML
    * recommended program options e.g. IQTREE Ultrafastbootstrap
* Virtues of each one: speed, ease of use, documentation
* Newick file format and manipulation of
* Assessment: support values
* Visualisation

### Estimating the species tree
* Choice of program
* Assessment: support values
* Visualisation

The following links to tutorials go into further details about processing read data and estimating trees. Some additional computing knowledge required and is  discussed in the next section.
* Sidonie's workflow
* Ben's workflow  

## Computing requirements and software

## Skeleton workflow summary
This section is a very short summary of the commands required for a complete analysis. It will take the example data set from HybPiper work through read preparation, HybPiper gene recovery, gene alignment with MAFFT, gene tree estimation with IQTREE2 and ASTRAL tree for estimating the species tree





Add in my refs!!!! from Evernote?


---
<span style="font-size:small;">Copyright © 2024 The Board of Trustees of the Royal Botanic Gardens, Kew</span>



