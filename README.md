# 2019-final-project

## Section 1: Description
Lung Cancer Is the Biggest Cancer Killer in Both Men and Women. Every year, about 200,000 people are diagnosed and 150,000 people die. 
Adenomas and adenocarcinomas is the most commom type of lung cancer nowadays. I want to know how genes express differently between Adenomas and adenocarcinomas lung cancer tissues and normal lung tissues. So I plan to do a typical RNA-sequencing analysis about **lung cancer (Adenomas and adenocarcinomas)** following steps as below, with the results obtained informing future experiments and validation studies, using three popular packages from Bioconductor as mentioned in the article. https://www.bioconductor.org/packages/devel/workflows/vignettes/RNAseq123/inst/doc/limmaWorkflow.html#data-packaging

## Section 2: Datasets
TCGA dataset (30 primary tumor RNA-seq files vs 30 solid tissue normal RNA-seq files) <br>
Exporation: <br>
Primary Site: bronchus and lung<br>
Disease Type: adenomas and adenocarcinomas<br>
Experimental Strategy: RNA-Seq<br>
Sample Type: primary tumor/solid tissue normal<br>
_View files in respository_<br>
Respository: <br>
Data Category: transcriptome profiling<br>
Data Type: Gene Expression Quantification<br>
Workflow Type: HTSeq-Counts<br>
Primary tumor: https://portal.gdc.cancer.gov/repository?filters=%7B%22op%22%3A%22and%22%2C%22content%22%3A%5B%7B%22content%22%3A%7B%22field%22%3A%22cases.case_id%22%2C%22value%22%3A%5B%22set_id%3AAW5D0bRk3lRTKaHL2A6c%22%5D%7D%2C%22op%22%3A%22IN%22%7D%2C%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22files.analysis.workflow_type%22%2C%22value%22%3A%5B%22HTSeq%20-%20Counts%22%5D%7D%7D%2C%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22files.experimental_strategy%22%2C%22value%22%3A%5B%22RNA-Seq%22%5D%7D%7D%5D%7D<br>
solid tissue normal: https://portal.gdc.cancer.gov/repository?filters=%7B%22op%22%3A%22and%22%2C%22content%22%3A%5B%7B%22content%22%3A%7B%22field%22%3A%22cases.case_id%22%2C%22value%22%3A%5B%22set_id%3AAW5D1nGdLao0-TEkdbYN%22%5D%7D%2C%22op%22%3A%22IN%22%7D%2C%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22files.analysis.workflow_type%22%2C%22value%22%3A%5B%22HTSeq%20-%20Counts%22%5D%7D%7D%2C%7B%22op%22%3A%22in%22%2C%22content%22%3A%7B%22field%22%3A%22files.experimental_strategy%22%2C%22value%22%3A%5B%22RNA-Seq%22%5D%7D%7D%5D%7D<br>
The 30 front files listed are all open, so I downloaded them as input seperately.<br>

## Proposed Analysis
### 1, Data packaging:  <br>
Download 30 primary adenomas and adenocarcinomas lung tumor RNA-seq files and 30 solid tissue normal RNA-seq files available online from dataset above, combine them into a matrix of counts using **edgeR**, then converted into a DGEList-object using the DGEList function.
Retrieve the second data frame named genes in the DGEList-object using organism specific packages **Homo.sapiens** (Bioconductor Core Team 2016a) for human.<br>
The ensembl gene names available in our dataset were annotated using the Homo.sapiens package to retrieve associated gene symbols and chromosome information.
### 2, Data pre-processing:  <br>
Raw counts are converted to CPM and log-CPM values using the cpm function in edgeR. The filterByExpr function in the edgeR package provides an automatic way to filter genes, while keeping as many genes as possible with worthwhile counts.<br>
Normalisation by the method of trimmed mean of M-values (TMM) (Robinson and Oshlack 2010) is performed using the calcNormFactors function in **edgeR** . <br>
The multi-dimensional scaling (MDS) plot can be made in limma using the plotMDS function. Alternatively, the **Glimma** package offers the convenience of an interactive MDS plot where multiple dimensions can be explored. 
### 3, Differential expression testing:<br>
Create a design matrix and contrasts. Contrasts for pairwise comparisons between cell populations are set up in **limma** using the makeContrasts function. <br>
Genes that are DE in multiple comparisons can be extracted using the results from decideTests.
Produce an interactive display which allows the user to search for particular genes based on the annotation provided, by **Glimma** showing results for all genes visually, mean-difference plots, which display log-FCs from the linear model fit against the average log-CPM values (mean-difference plot).<br>
A heatmap is created for the top 100 DE genes (as ranked by adjusted p-value) from the basal versus LP contrast using the heatmap.2 function from the **gplots** package.

## Proposed Timeline & Major milestones (or segments)<br>
Milestone 1(11/13/19): Finish proposed step 1<br>
Milestone 2(11/20/19): Finish proposed step 2<br>
Milestone 3(11/27/19): Finish proposed step 3, summarize results <br>

## User Interface
 https://www.bioconductor.org/packages/devel/workflows/vignettes/RNAseq123/inst/doc/glimma-plots/MD-Plot.html

