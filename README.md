# drosophila-rnaseq-galaxy
RNA-Seq analysis of Drosophila using Galaxy platform
# Drosophila RNA-Seq Analysis: Amino Acid Starvation Response 🧬

## What this is
This project looks at how Drosophila melanogaster responds to amino 
acid starvation at the gene expression level, using RNA-Seq data analyzed 
on Galaxy, a browser-based platform that runs a full RNA-Seq pipeline 
(from raw reads to differential expression) without needing to write code, 
while still following the same steps used in command-line workflows.

This was one of my earlier projects, and it's where I first got hands-on 
with real RNA-Seq data, network analysis, and pathway enrichment instead 
of just reading about them in coursework.

## The question I was trying to answer
How does amino acid starvation change gene expression in Drosophila cells, 
and what biological processes and pathways are involved in that response?

## How I approached it
1. **Quality check** :ran FastQC on the raw reads to confirm the data 
   was clean before analysis
2. **Alignment** : mapped reads to the Drosophila reference genome using 
   HISAT2
3. **Quantification** : counted reads per gene with featureCounts
4. **Differential expression** : used DESeq2 to compare starved vs. 
   normal (control) conditions and identify significantly upregulated genes
5. **Functional enrichment** : ran GO and KEGG enrichment on the 
   upregulated genes to understand what biological processes they're 
   involved in
6. **Protein-protein interaction (PPI) network** : built an interaction 
   network with STRING to see how the affected proteins relate to each 
   other
7. **Hub gene analysis** : used Cytoscape (CytoHubba, MCC method) to 
   identify the most highly connected "hub" proteins in that network

## What I found
- Amino acid starvation caused a clear shift in gene expression compared 
  to the control condition, with a set of genes consistently upregulated
- **GO enrichment** pointed strongly toward mitochondrial components and 
  functions suggesting starvation affects mitochondrial activity and 
  energy metabolism. Terms related to cell division and meiotic processes 
  also came up, hinting at effects on growth/reproductive functions
- **KEGG enrichment** showed involvement of DNA replication, RNA 
  polymerase, cell cycle, p53 signaling, cytosolic DNA sensing, and 
  beta-alanine metabolism indicating the starvation response isn't 
  driven by a single pathway but touches multiple cellular systems at once
- **STRING PPI network** contained 464 proteins and 1,832 interactions 
  (confidence score ≥ 0.700), showing that many of the affected proteins 
  work closely together rather than independently
- **Hub gene analysis** identified the top connected proteins in this 
  network — including CG11837, CG7246, wcd, CG1789, CG6937, Sas10, NHP2, 
  CG9246, l(2)05287, and CG4806 as potential key players worth further 
  investigation

## Tools
Galaxy · FastQC · HISAT2 · featureCounts · DESeq2 · STRING · Cytoscape 
(CytoHubba)

## Limitations
This analysis used only two biological replicates, which limits the 
statistical power of some results. The GO, KEGG, and PPI findings are 
also based on existing annotations and predicted interactions so while 
they point to interesting candidate genes and pathways, they'd need 
experimental follow up to confirm actual biological roles.

## Files in this repo
- `GUI-RNA seq report.pdf` the complete write up, including methodology, 
  all results/figures, and discussion

## A note on the approach
This analysis was done entirely through Galaxy's GUI rather than the 
command line. I've since moved on to running similar pipelines directly 
in Linux/bash for more control and reproducibility you can see that 
work in my other repositories.
