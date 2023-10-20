# MI_13Cytokines_12Stim

This repository contains all reproductible scripts to generate the figures presented in the article:

Please cite this article when using this code. 

Contact: violaine.saint-andre@pasteur.fr

The source code was developed and tested using R 4.2.1 in R Studio on masOS Monterey version12.4.

These scripts are made available under the GPL3 license. Se the LICENSE file for details.

The user can upload the archive folder containing all the files . This should only take a few minutes on a "normal" desktop computer.

Each R script refers to the Figure in its title and can run independently of the others.The input files containing the source data are:
- TableS1.txt: Luminex proteomic data (Supplementary Table 1 of the article)  
- TableS2.txt: eCRF variables (Supplementary Table 2 of the article) 
- df_datavarShort.txt: Description of the eCRF variables
- facs_counts_renamed.txt: Cellular counts of 76 cell subsets

There is no demo data as the code can run in a few minutes on the real data that can be made public.

The result files will be generated in the empty RESULTS folder contained in the archive and should reproduce the corresponding figures of the article.

Pseudocode details of each script:

- Fig1a:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data 
Compute standardized log mean difference between each stimulated condition and the Null for each cytokine
Plot the heatmap, rearrange and color the dendrogram

- Fig1c_2:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data 
Import eCRF variables and set categorical and numerical variables
For in each stimulation, run Likelihood Ratio Tests  between each eCRF variable and each cytokine considered expressed and record data for effect size plots
Apply exception to select for responders only for CD3+CD28 and to remove TNFa in TNFa stimulation, IL1b in IL1b stimulation and IFNg in IFNg stimulation
Correct for multiple testing using BY on the full matrix
Plot heatmaps for the eCRF variables that have at least one cytokine associated (BY adjusted p-value < 0.01)
Create effect size plots for each level of  the smoking related variables
Color differently significant and non-significant effect sizes
Create boxplots for CXCL5 in E.coli and LPS and IL2 in SEB and CD3+CD28 stimulations depending on the smoking status variable
Add Wilcoxon test adjusted p-values
Create scatterplots of expressed cytokines in E.coli, LPS, SEB and CD3+CD28 stimulations depending on the number of years smoking variable
Add linear regression lines and confidence intervals
This code was also used to create panels a, b and c of FigS6

- Fig3a:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Upload the cellular data and log transform them
Import eCRF variables and set categorical and numerical variables
For each  SEB or E.coli stimulations run Likelihood Ratio Tests  between the smoking variable and each cytokine considered expressed in the stimulation considering cell subset counts or none as covariates (with interaction terms) and correcting for age sex and batchId 
Correct for multiple testing using BY on the full matrix 
Plot a heatmap by stimulation for all tested variables

- Fig3b:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import eCRF variables and set categorical and numerical variables
For each SEB or E.coli stimulations run Likelihood Ratio Tests  between the smoking variable and each cytokine considered expressed considering plasma protein levels or none as covariates (with interaction terms) and correcting for age sex and batchId 
Correct for multiple testing using BY on the full matrix
Plot effect sizes corresponding to these regressions

- Fig4:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import eCRF variables and set categorical and numerical variables
Upload the DNA methylation data
Create boxplots for significant probes depending on the smoking status variable
Add Wilcoxon test adjusted p-values
Create scatterplots of DNA methylation levels dependent on the smoking related variables and IL2 in the SEB stimulation
Add linear regression lines and confidence intervals

- Fig5:
Import proteomic matrix, removed donors that have been reprocessed and log transform the data
Apply exception to select for responders only for CD3+CD28 
Upload the cellular data and log transform them
Import eCRF variables and set categorical and numerical variables
For each stimulation compute the variance explained by each associated factor and create barplots

- FigS1:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data 
Import eCRF variables  
Create a biplot for all the stimulations colored by stimulation
Create biplots by stimulation for each smoking, age, sex, season and batchId variable

- FigS2:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
For each stimulation perform clustering with ward.D method and use same scale for all to plot heatmaps of proteomic data with heatmap.2
Open the pdf with adobe for best colors

- FigS3:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Apply exception to select for responders only for CD3+CD28 
Import eCRF variables and set categorical and numerical variables
For each stimulation run Likelihood Ratio Tests  between each eCRF variable and each cytokine considered expressed 
Correct for multiple testing using BY on the full matrix
Plot heatmaps for the eCRF variables that have at least one cytokine associated (BY adjusted p-value < 0.01)

- FigS4_S5:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import eCRF variables and set categorical and numerical variables
For each stimulation run Likelihood Ratio Tests  between age or sex variable and each cytokine considered expressed correcting for batchId
Correct for multiple testing using BY on the full matrix
Plot heatmaps of BY adjusted p-values of association between age and sex variables and each cytokine considered expressed 
Create Effect size plots for age and sex on each cytokine considered expressed
Color the confidence intervals depending on the significance of the effect sizes
Add stars depending on the Likelihood Ratio Tests p-values

- FigS6: 
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import eCRF variables and set categorical and numerical variables
For E.coli, LPS, SEB, CD3+CD28 stimulations, regress the proteomic data on age, sex and batchId
Create boxplots for CXCL5 in E.coli and LPS and IL2 in SEB and CD3+CD28 stimulations depending on the smoking status variable
Add Wilcoxon test adjusted p-values
Create scatterplots of the residues in E.coli, LPS, SEB and CD3+CD28 stimulations depending on the number of years smoking variableAdd linear regression lines and confidence intervals

- FigS7a:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Upload the cellular data and log transform them
Import eCRF variables and set categorical and numerical variables
For SEB stimulation run Likelihood Ratio Tests between the CMV variable and proteomic data considering cell subset numbers or none as covariates correcting for age sex and batchId 
Correct for multiple testing using BY on the full matrix
Plot a heatmap for all tested cell subsets and none with each of the expressed cytokines

- FigS7b:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Upload the  methylation data and log transform them
Import eCRF variables and set categorical and numerical variables
For SEB stimulation run Likelihood Ratio Tests  between each methylation probe and  IL2 using age sex and batchId as covariates
Correct for multiple testing using BY on the full matrix
Select the probes that have a BY corrected p-value < 0.01
For SEB stimulation run Likelihood Ratio Tests  between the smoking variable and IL2 using the 129 methylation probe or none as covariates correcting for age sex and batchId 
Correct for multiple testing using BY on the full matrix
Plot a heatmap of the corrected p-values for each of the 129 tested probe with each of the expressed cytokines

- FigS8:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import eCRF variables and  the cis and trans pQTLs
For each stimulation compute Likelihood Ratio Tests for interractions between the smoking variable and the SNPs correcting for age sex and batchId 
Correct for multiple testing using BY on the full matrix
Plot heatmaps of corrected p-values for each SNP:smoking interaction
Create corresponding effect size plots for each  interaction 
Color differently significant and non-significant effect sizes
Plot boxplots  of IL8 levels depending on the smoking status for a specific SNP

- FigS9:
Import proteomic matrix, remove donors that have been reprocessed and log transform the data
Import trans SNPs data
Separate responders versus non responders with k-means clustering
Plot boxplots of IL2 expression depending on rs1801274 before and after selection of the responders


