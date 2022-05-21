---
template: blog_post.html
title: 1000 Genomes CNV data
description: A WGS-based reference dataset representing CNVs in the 1000 Genome samples 
date: 2022-05-20
authors:
  - "@ziyingyang96"
  - "@mbaudis"
hide:
  - navigation
  - toc
---


In October 2020, the _AWS for Industries_ group (authored by Bryan Lajoie, Staff Bioinformatics Scientist at Illumina Inc.) published a re-analysis of 3202 deep WGS sequencing datasets from the _1000 Genomes Project_, freely available for download by interested researchers. 


Based on a set of well defined samples, this data can be considered a "high-quality resource for germline CNV data", for disease and population analysis projects.


 in observed in the "1000 genomes". An international effort that began in 2008, 1kGP addressed a community need to identify and catalog normal genetic variation across diverse populations with the current dataset representing 2504 individuals from 26 populations as well as the recent addition of genomes for another 698 related individuals, completing 535 parent-child triads, as well as other non-triad pedigrees. The 1kGP remains one of the most diverse and widely used references for naturally occurring genetic variation in human populations. With over 5400 citations in the scientific literature to date, the 1kGP is regarded as “an essential tool” for genomic studies ranging from the evolutionary history of humankind to elucidating molecular mechanisms such as linkage disequilibrium and genetic recombination to the discovery and validation of disease-associated genetic mutations. For example, 1kGP data played an important role in the development of a sequence-based tool that identifies copy number variation in the SMN1 and SMN2 genes, which are used as genetic markers for Spinal Muscular Atrophy (SMA) risk. Researchers  used 1kGP data to assess SMN1 and SMN2 variants copy number variation (CNV), and the identification of variant sites that can be used to reliably differentiate the two close paralogs SMN1 and SMN2 across all populations.

While the CNV data of the 1000 genomes project is of increasing utility for research into genetic diseases and cancer, so far the genomic data has been stored in VCF files, which may be inconvenient for researchers to access, download or process. As part of our work on bioinformatics tools and online resources for the Progenetix repository and as part of the Beacon project of the Global Alliance for Genomics and Health (GA4GH) and  ELIXIR, our group is working on a dedicated VCF converter tool to transfer VCF into data objects for storage and retrieval using emerging technologies and GA4GH derived standards.

We build an online accessible database 1000genomesDRAGEN website to store these CNV data and to provide a Beacon-compatible API, thereby enabling federated access to this reference data using an accepted GA4GH data standard. The 1000genomesDRAGEN database provides an overview of mutation data in cancer, with a focus on copy number abnormalities (CNV / CNA), for all types of human malignancies. The data is based on individual sample data from currently 3200 samples from the “1000 genomes project”. Besides the API access, users will be presented with a web interface, to search the variants, download the data, do online analyses and retrieve the visualization of the results. 

The content of the 1000genomesDRAGEN resource is freely accessible for research and commercial purposes, with attribution. The database & software are developed by the group of Michael Baudis at the University of Zurich and the Swiss Institute of Bioinformatics [(SIB)]http://sib.swiss/baudis-michael/”. Many previous members and external collaborators have contributed to data content and resource features. Participation (features, data, comments) by volunteers are welcome.
