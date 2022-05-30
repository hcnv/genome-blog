---
template: blog_post.html
title: Types of Genomic Copy Number Variations
description: Classification of CNVs based on CN level and genomic size
date: 2022-05-30
authors:
  - "@hangjiaz"
  - "@mbaudis"
hide:
  - navigation
  - toc
---

Genomic copy number variations can affect the production of proteins through their modification
of the "dosage" (i.e. number of alleles) of genes covered by the CNV as well as through the
(in)complete disruption of coding or regulatory elements. The supposed effects depend on the
magnitude of change, _i.e._ the number of gained or lost copies. Especially in cancer cells the
"normal" allele count for the given genomic region has to be considered: Cancer genomes may have undergone
general anaeuplodization events with preceding and/or followed by regional CNV events.

Copy number changes can be expressed as absolute (total allele count) and relative (e.g. uncalibrated CN measurements
such as log2 ratio) values. Empirically - and to overcome a number of issues of exact CN count
calibrations - a classification into a number CN types has become "standard operating procedure" with details
differing to some extent. This post attempts to summarize some previous annotation practices
and emerging standards for CNV annotation, especially with respect to somatic CNVs and cancer genomics.

<!--more-->

Additional measures which have been used in some of those classification attempts have been:

1. the locality of additional copies of genomic regions in gain CNVs
2. the size of the CNV events
3. an overall context or inferred mechanism

Here we will mostly consider 2 - the CNV size - where it makes sense; the locality or overall
mechanism (such as "chromothripsis", "katagesis" etc.) constitute special cases which in some cases (e.g.
many tandem duplications) can be considered gene specific structural alterations more than "dosage events".

Regarding the CNV size, CNVs can broadly be separated into "cytogenetic" or
"arm-level" changes[^1] which arise from errors in chromosomal distribution during cellular division
with or without structural chromosomal rearrangements, and "focal" CNVs based on DNA replication errors with smaller
(_i.e._ [sub-]megabase) deletions or (intra or extrachromosomal) multi-copy duplications[^2]. While the role of
disease-related, arm- and chromosome-level CNVs in cancer still is poorly understood, focal CNVs frequently
involve the genomic locations of genes with known involvement in neoplastic processes.

Importantly, the magnitude of these CNV size classes may differ. All arm-level gain CNVs and many focal CNVs
have a low divergence in CN count while some focal CNVs can reach very high relative magnitude, such as an amplification
with tens or hundreds of copies. However, the definition of genomic amplification is ambiguous. Generally, it means multiple copies of chromosomal segments, but the exact copy number threshold to define amplification is not consistent in multiple studies, varying from 4 to 9 or more (Table 1). 

For deletions, the definition of high-magnitude deletion is clear. It usually represents a complete loss of 
genomic elements and relevant functions. 

### Purported Effects of CNV "Classes" in Oncogenomics

The observation that high-amplitude focal CNVs often occur in specific regions where tumor 
oncogenes and suppressor genes locate indicates that this type of CNV is possible to contain 
the optimal chromosomal segments for promotion of cancer development and thus has great power 
to discover cancer-related genes. The prevalence of low-amplitude chromosomal arm-level CNVs
in cancer patients shows a close relationship between CNV and molecular properties of cancer cells. 
The length and amplitude of somatic CNVs determine distinct classes of somatic CNVs. They are 
different in occurrence frequency and impact on genomic components. A better understanding of 
both types of somatic CNVs is important and required. Currently, there are several standards and ontologies to 
specify different classes of CNV. More details can be found in the comparison table 2 (taken from the [Beacon v2 documentation](http://docs.genomebeacons.org/variant-queries/#term-use-comparison)).

### Varying Definitions of "High Level" Gain CNVs

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


## A CNV Classification Based on Relative CN Alterations

In 2021 - based on a recognized need to formalize the representation of relative CN value classes
as a concept capturing general usage scenarios from cancer genomics and genetics while
accommodating different data generation practices - we proposed a set of basic CNV classes for
adoption by the Experimental Factor Ontology, following discussions with members of the hCNV community
and the GA4GH Variant Representation Standard working group.

### Term Use Comparison

| Beacon | [VCF](https://samtools.github.io/hts-specs/) | SO | [EFO](http://www.ebi.ac.uk/efo/EFO_0030063) | [VRS](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) | Notes   |
| -------|-----|----|-----|-----|---------|
| `DUP`    | `DUP`[^3] | [`SO:0001742`](http://www.sequenceontology.org/browser/current_release/term/SO:0001742) copy_number_gain | [`EFO:0030070`](http://www.ebi.ac.uk/efo/EFO_0030070) copy number gain | [`low-level gain`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) (implicit) | a sequence alteration whereby the copy number of a given genomic region is greater than the reference sequence |
| `DUP`    | `DUP`[^3] | [`SO:0001742`](http://www.sequenceontology.org/browser/current_release/term/SO:0001742) copy_number_gain |[`EFO:0030071`](http://www.ebi.ac.uk/efo/EFO_0030071) low-level copy number gain | [`low-level gain`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) |  |
| `DUP`    | `DUP`[^3] | [`SO:0001742`](http://www.sequenceontology.org/browser/current_release/term/SO:0001742) copy_number_gain |[`EFO:0030072`](http://www.ebi.ac.uk/efo/EFO_0030072) high-level copy number gain | [`high-level gain`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber)  | commonly but not consistently used for >=5 copies on a bi-allelic genome region |
| `DUP`    | `DUP`[^3] | [`SO:0001742`](http://www.sequenceontology.org/browser/current_release/term/SO:0001742) copy_number_gain |[`EFO:0030073`](http://www.ebi.ac.uk/efo/EFO_0030073) focal genome amplification | [`high-level gain`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber)  | commonly but not consistently used for >=5 copies on a bi-allelic genome region, of limited size (operationally max. 1-5Mb) |
| `DEL`    | `DEL`[^3] | [`SO:0001743`](http://www.sequenceontology.org/browser/current_release/term/SO:0001743) copy_number_loss | [`EFO:0030067`](http://www.ebi.ac.uk/efo/EFO_0030067) copy number loss | [`partial loss`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) (implicit) | a sequence alteration whereby the copy number of a given genomic region is smaller than the reference sequence | 
| `DEL`    | `DEL`[^3] | [`SO:0001743`](http://www.sequenceontology.org/browser/current_release/term/SO:0001743) copy_number_loss | [`EFO:0030068`](http://www.ebi.ac.uk/efo/EFO_0030068) low-level copy number loss | [`partial loss`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) | |
| `DEL`    | `DEL`[^3] | [`SO:0001743`](http://www.sequenceontology.org/browser/current_release/term/SO:0001743) copy_number_loss | [`EFO:0030069`](http://www.ebi.ac.uk/efo/EFO_0030069) complete genomic deletion | [`complete loss`](https://vrs.ga4gh.org/en/latest/terms_and_model.html#relativecopynumber) | complete genomic deletion (e.g. homozygous deletion on a bi-allelic genome region) |


[^1]: This represents an approximation and doesn't try to address the - fascinating - biology of genomic rearrangements such as chromothripsis, katagesis etc. Maybe another time...
[^2]: Beroukhim, Rameen, et al. "The landscape of somatic copy-number alteration across human cancers." Nature 463.7283 (2010): 899-905.
[^3]: VCFv4.4 introduces an `SVCLAIM` field to disambiguate between _in situ_ events (such as
tandem duplications; known _adjacency_/ _break junction_: `SVCLAIM=J`) and events where e.g. only the
change in _abundance_ / _read depth_ (`SVCLAIM=D`) has been determined. Both **J** and **D** flags can be combined.
