# 2019-final-project

## Section 1: Description
RNA has intrinsic propensity to form base pairs, leading to complex intramolecular and intermolecular helices. Direct measurement of base pairing interactions in living celss is critical to solve transcriptome structure and interactions, and investigating their function. Toward this goal, we developed an experimental method, PARIS(Psoralen Analysis of RNA Interactions and Structures) to directly determine transcriptome-wide base paring interactions (Lu et al., Cell 165(5):1267-1279,2016). This time, I plan to analyze one set of PARIS data from one sample of HEK293 cells, to see the global mapping of RNA duplexes in living cells, including extensive long-range structures, higher-order architectures, alternative structures, and RNA-RNA interactions. 
## Section 2: Datasets
This data is from our lab, produced on 05/25/2019. It is sequenced on Illumina miseq using standard conditions and the P6_Custom_seqPrimer. Sequencing data are RNA-seq, and provided in zipped fastq files.
## Proposed Analysis
1, Remove the adapter sequences (using Trimmomatic)
2, Remove the duplicates (from the icSHAPE pipeline)
3, Split the trimmed and collapsed libraries using splitFastqLibrary
4, Remove random and multiplexing barcodes (using Trimmomatic)
5, Generate reference index 
6, Map reads to a genome index of choice using STAR
7, Convert SAM to BAM format, sort the BAM file and extract primary mapped reads using SAMtools
8, Extract gapped reads from the Aligned.out_sorted.bam file
## Proposed Timeline & Major milestones (or segments)
Milestone 1(11/13/19): Finish proposed step 1-3
Milestone 2(11/20/19): Finish proposed step 4-6
Milestone 3(11/27/19): Finish proposed step 7-8, write summary of results (different type of RNA duplexes)
## User Interface
? Make a R? 
