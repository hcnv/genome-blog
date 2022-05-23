---
template: blog_post.html
title: 1000 Genomes CNV reference data 
description: An API for the WGS-based reference dataset of CNVs in the <i>1000 Genomes</i> samples 
date: 2023-05-20
authors:
  - "@ziyingyang96"
  - "@mbaudis"
hide:
  - navigation
  - toc
---

In October 2020, the _AWS for Industries_ group [published](https://aws.amazon.com/blogs/industries/dragen-reanalysis-of-the-1000-genomes-dataset-now-available-on-the-registry-of-open-data/) a re-analysis of 3202 deep WGS sequencing datasets from the _1000 Genomes Project_ (1kGP), freely available for download by interested researchers and including the copy number variations (CNV) inferred for these genomes. Based on a set of well defined samples, this data can be considered a "high-quality resource for germline CNV data", for disease and population analysis projects. Now, this data is being made available though the [Progenetix resource's API](http://progenetix.org/progenetix-cohorts/oneKgenomes/).

!!! info "1000 Genomes Germline CNVs on Progenetix"

    ##### LINK: <http://progenetix.org/progenetix-cohorts/oneKgenomes/>

<!--more-->

**Background** As an international, collaborative effort, since 2008 the _1kGP_ has worked on the identification and characterization of "normal" genetic variation across diverse populations. The current dataset represents the original 2504 individuals from 26 populations as well as recently added genomes for 698 individuals with genetic relations, containing 535 parent-child triads as well as other non-triad pedigrees. The 1kGP remains one of the most widely used references for naturally occurring genetic variation in human populations. With over 5400 citations in the scientific literature to date, the 1kGP is regarded as “an essential tool” for genomic studies ranging from the evolutionary history of humankind to elucidating molecular mechanisms such as linkage disequilibrium and genetic recombination to the discovery and validation of disease-associated genetic mutations.

While a large part of the _1kGP_ utilization has been based on its representation of single nucleotide variants (SNPs) as well as their linkage, the WGS data has also been used to map CNVs and to utilize this information for the identification of CNV-related diseases. For example, 1kGP data played an important role in the development of a sequence-based tool that identifies copy number variation in the _SMN1_ and _SMN2_ genes, which are used as genetic markers for Spinal Muscular Atrophy (SMA) risk. Researchers used _1kGP_ data to assess SMN1 and SMN2 copy number variation variants (CNV), and the identification of variant sites that can be used to reliably differentiate the two close paralogs SMN1 and SMN2 across all populations.

**Data Formats** While the CNV data of the 1000 genomes project is of high utility for research into genetic diseases and cancer, so far the genomic data has been stored in VCF files, which may be inconvenient for many use cases (e.g. fast lookup of CNVs for a specific location) and also be affected by ambiguities in VCF parsing for CNVs and other structural variants. As part of our for the Progenetix repository and related to the Beacon project of the Global Alliance for Genomics and Health (GA4GH) and  ELIXIR, the _Computational Cytogenetics and Cancer Genomics_ group at the University of Zurich and SIB has implemented a version of the _1kGP_ CNV dataset, accessible through the Progenetix BeaconPlus API. At this time (May 2022) both the (still internal) VCF conversion tools as well as the data should be considered "under construction" and awaiting community feedback. Particularly, the final format may undergo changes based on the emerging representation of relative and absolute CNV values in the GA4GH VRS standard.

**API** The Progenetix resource provides an overview of mutation data in cancer, predominantly as the largest public resource of curated copy number abnormalities (CNV / CNA), for all types of human malignancies. Integrated into the Progenetix framework, we built an online _oneKgenomes_ cohort with a dedicated landing page and a Beacon v2 compatible API and to enable federated access to this reference data using a recently accepted accepted GA4GH data standard. Besides the API access, users will be presented with a web interface, to search the variants, download the data, do online analyses and retrieve the visualization of the results. The data is based on currently 3202 samples from the Illumina DRAGEN re-analysis of the 1000 genomes project's deep WGS data on the AWS platform.  

The content of our _oneKgenomes_ resource is freely accessible for research and commercial purposes, with attribution. For feedback and inquiries you are welcome to [contact us](http://info.baudisgroup.org). Also, participation (features, data, comments) in the different aspects of the [Progenetix project](http://github.com/progenetix/) by volunteers is always welcome! More information about the [Progenetix API](http://docs.progenetix.org) and the [Beacon v2 standard](http://docs.genomebeacons.org) are avaible through their respective documenttaion pages.

!!! info "DRAGEN reanalysis of the 1000 Genomes Dataset"

    ### DRAGEN reanalysis of the 1000 Genomes Dataset now available on the Registry of Open Data
    #### Erin Chu, DVM, Ph.D. and Aaron Friedman, PhD
    ##### Guest authored by Bryan Lajoie, Staff Bioinformatics Scientist at Illumina Inc.

    AWS for Industries [blog post](https://aws.amazon.com/blogs/industries/dragen-reanalysis-of-the-1000-genomes-dataset-now-available-on-the-registry-of-open-data/)


!!! note "Testing Beacon + VRS responses for 1kGP variants"

    Below is an excerpt showing the (May 2022) representation of a 1kGP variant
    through the Progenetix BeaconPlus API.
    Call: <https://progenetix.org/beacon/biosamples/onekgbs-HG00142/g_variants>
  
    ```
        "results": [
          {
            "caseLevelData": [
              {
                "analysisId": "onekgcs-HG00142",
                "biosampleId": "onekgbs-HG00142",
                "id": "onekgvar-606ea3418c2f487fffadbcb7"
              }
            ],
            "variation": {
              "location": {
                "interval": {
                  "end": {
                    "type": "Number",
                    "value": 45516759
                  },
                  "start": {
                    "type": "Number",
                    "value": 45508890
                  }
                },
                "sequence_id": "refseq:NC_000012.12",
                "type": "SequenceLocation"
              },
              "relative_copy_class": "partial loss",
              "updated": "2022-05-13 09:13:08.050000",
              "variantInternalId": "12:45508890-45516759:DEL"
            }
          }
        ]
    ```

