---
template: blog_post.html
title: Types of Genomic Copy Number Variations
description: Classification of CNVs based on CN level and genomic size
date: 2022-05-23
authors:
  - "@hangjiaz"
  - "mbaudis"
hide:
  - navigation
  - toc
---

Genomic copy number variations can be quantified in two general dimensions - through their size
and through the divergence from the expected regional allele count. Both of these quantities can be expressed as absolute (e.g. base count,
total allele number) and relative (e.g. chromosomal fraction involved, uncalibrated CN measurement
value such as log2 ratio) values. Empirically - and to overcome a number of issues of exact CN count
calibrations - a classification into a number CN types has become "standard opreating procedure" although
the details of those classes differ to some extend. This post attempts to summarize some previous annotation practices
and emerging standards for CNV annotation, especially with respect to somatic CNVs and cancer genomics.

<!--more-->

With various types of molecular accidents leading to regional changes in the number of copies
of alleles from a given genomic region, such CNVs can broadly be separated into "cytogenetic" or
"arm-level" changes[^1] which arise from errors in chomosomal distribution during cellular division
with or without structural chromosomal rearrangements, and "focal" CNVs based on DNA replication errors with smaller
(_i.e._ [sub-]megabase) deletions or (intra or extrachromosomal) multi-copy duplications[^2]. While the role of
disease-related, arm- and chromosome-level CNVs in cancer still is poorly understood, focal CNVs frequently
involve the genomic locations of genes with known involvement in neoplastic processes.



The background rates of both size classes of somatic CNVs are different. The occurrence of focal CNVs is negatively 
associated with their length. Arm-level CNVs occur more frequently than expected by the inverse-length 
distribution related to focal CNVs, which applies to all cancer types.

The amplitudes of 
these somatic CNVs are also not the same. All arm-level CNVs and many focal CNVs are of low amplitude 
while some focal CNVs can reach very high amplitude, such as amplification or homozygous deletion. 
The definition of high-amplitude deletion is clear. It usually represents a complete loss of 
genomic elements and relevant functions. However, the definition of amplification is ambiguous. 
Generally, it means multiple copies of chromosomal segments, but the exact copy number threshold 
to define amplification is not consistent in multiple studies, varying from 4 to 9 or more flexible (Table 1). 

#### Varying Definitions of "High Level" Gain CNVs

|  Study ID & link | Study name| Threshold (>=) | 
| ---- | ---- | :--: |
| [PMID21494657](https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0018369) | Network-Guided Analysis of Genes with Altered Somatic Copy Number and Gene Expression Reveals Pathways Commonly Perturbed in Metastatic Melanoma | 4 |   
| [PMID17161620](https://www.sciencedirect.com/science/article/pii/S1044579X06000988?via%3Dihub) | Specificity, selection and significance of gene amplifications in cancer | 5 |    
| [PMID32024823](https://www.nature.com/articles/s41467-019-13885-w) | High-coverage whole-genome analysis of 1220 cancers reveals hundreds of genes deregulated by rearrangement-mediated cis-regulatory alterations | 5 |    
| [PMID25719666](https://www.nature.com/articles/nature14169) | Whole genomes redefine the mutational landscape of pancreatic cancer | 6 |   
| [DOI:10.1036/ommbid.321](https://ommbid.mhmedical.com/content.aspx?bookId=2709&sectionId=225073577)  | Gene Amplification in Human Cancers: Biological and Clinical Significance| 7 |
| [PMID25110350](https://www.sciencedirect.com/science/article/pii/S0167488914003000?via%3Dihub) | Focal chromosomal copy number aberrations in cancer—Needles in a genome haystack | 9 |   
| [COSMIC database](https://cancer.sanger.ac.uk/cosmic/help/cnv/overview) | | 5 if ploidy <= 2.7 <br> 9 if ploidy > 2.7 |   
| [PMID28445112](https://www.nejm.org/doi/10.1056/NEJMoa1616288) | Tracking the Evolution of Non–Small-Cell Lung Cancer | 2 x ploidy + 1 |   
| [PMID28104840](https://www.science.org/doi/10.1126/science.aaf8399) | Tumor aneuploidy correlates with markers of immune evasion and with reduced response to immunotherapy | logR >= 1 | 
  
The observation that high-amplitude focal CNVs often occur in specific regions where tumor 
oncogenes and suppressor genes locate indicates that this type of CNV is possible to contain 
the optimal chromosomal segments for promotion of cancer development and thus has great power 
to discover cancer-related genes. The prevalence of low-amplitude chromosomal arm-level CNVs
in cancer patients shows a close relationship between CNV and molecular properties of cancer cells. 
The length and amplitude of somatic CNVs determine distinct classes of somatic CNVs. They are 
different in occurrence frequency and impact on genomic components. A better understanding of 
both types of somatic CNVs is important and required. Currently, there are several standards and ontologies to 
specify different classes of CNV. More details can be found in the comparison table from [Beacon v2 documentation](http://docs.genomebeacons.org/variant-queries/#term-use-comparison).


[^1]: This represents an approximation and doesn't try to address the - fascinating - biology of genomic rearrangements such as chromothripsis, katagesis etc. Maybe another time...
[^2]: Beroukhim, Rameen, et al. "The landscape of somatic copy-number alteration across human cancers." Nature 463.7283 (2010): 899-905.
