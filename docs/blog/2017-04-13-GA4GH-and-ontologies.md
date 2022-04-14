---
template: blog_post.html
title: GA4GH implementation study - Making ontologies work
description: Diagnoses, phenotypes, species assignment and other “biocharacteristics” represented as “OntologyTerm” objects
date: 2022-04-03
author: "@mbaudis"
hide:
  - navigation
  - toc
---

!!! Note "Historical Post"

    This post appeared first (on WordPress hosted genome.blog) on 2017-04-13 and has been slightly edited to provide the evolution of the
    concepts. The post is a reminder of the history of some data structures now implemented throughout GA4GH aligned projects.

While developing the (metadata-)schema for the [Global Alliance for Genomics and Health](http://ga4gh.org), the Metadata Task Team decided (after, well, many hours of telecons) to use an object based model with a limited number of attributes. In place of specific, named attributes, emphasis is being put on the use of ontologies, which, in principle, provide their own scoping. Diagnoses, phenotypes, species assignment and other “biocharacteristics” were to be represented in as “OntologyTerm” objects, using schema-external ontology services such as EBI’s OLS.

<!--more-->

As part of a “human data implementation study” supported through ELIXIR, our group at the University of Zurich uses the data from our arraymap.org cancer genome resource, to test and implement genome and metadata representations compatible to a forward looking version of the GA4GH schemas.

In arrayMap, all of the currently >55,000 cancer genome datasets have been coded to the diagnostic codes (morphology and topography) from the International Classification of Diseases in Oncology (ICD-O 3). The internal representation using CURIE coding with an internal/unregistered “PGX” prefix of these ICD codes as GA4GH “Biocharacteristic” object is shown here[^1]:

=== "Updated Version - e.g. Progenetix 2022"

    ```json
    {
      "icdo_morphology": {
        "id": "pgx:icdom-94703",
        "label": "Medulloblastoma, NOS"
      },
      "icdo_topography": {
        "id": "pgx:icdot-C71.6",
        "label": "cerebellum"
      }
    }
    ```

=== "Original Version 2017"

    ```json
    "bio_characteristics" : [
      {
        "description" : "medulloblastoma",
        "ontology_terms" : [
          {
            "term_label" : "Medulloblastoma, NOS",
            "term_id" : "PGX:ICDOM:9470_3"
          },
          {
            "term_label" : "cerebellum",
            "term_id" : "PGX:ICDOT:C716"
          },
        ],
        "negated_ontology_terms" : [ ],
      },
    ]
    ```

However, we had to realize that the ICD-O classification, while having a shallow hierarchical component, right now is not an registered, open ontology and cannot be referenced through ontology services. Therefore, our own – rather well organized data – could not serve to exemplify ontology use in the GA4GH schema. And while ICD-O codes are represented in SNOMED-CT, their use is restricted through licensing; additionally the hierarchical component of the ICD derived codes are out of date and/or misleading.
NCIt to the rescue

Through their NCI Metathesaurus (NCIm), the National Cancer Institute (NCI) provides a wide-ranging biomedical terminology database. While the included terms describe concepts from various scopes, the “NCIt Neoplasm Core” (NPLcore) represents the most frequent neoplastic entities in a simplified hierarchy system, by site and morphology. We decided to add NCIt terms to all neoplastic samples in our arrayMap database, by using our previous in-house generated ICD coding to assign NCIt neoplasm core codes to unique combinations of ICD-O morphology and topography.

For our sample mapping (below), we used either the code from NPLcore, or a basic “tissue type” assignment, if the best code wasn’t represented in NPLcore (this seems somewhat circuitous, but will be required to represent the samples in the hierarchy).

Our [arrayMap](http://arraymap.progenetix.org)[^2] re-mapping currently leads us to 44915 mapped cancer genome arrays from GEO experiments (i.e., all have a NCBI GEO “GSM” identifier; other samples were re-mapped, too). The current representation in arrayMap does noy yet may use of the hierarchical representation; this is planned for the near future.

This is preliminary; we’ll be happy about corrections, suggestions etc. Also, the mapping should be considered a “living document”; we will probably expand & refine over time (& maybe switch to “NCIt first, ICD derived” approach.

The current mapping of arrayMap samples to the GA4GH schema is shown in our arraymap2ga4gh github repository – which will be topic of another post.

=== "Updated Version - e.g. Progenetix 2022"

    ```json
    {
      "icdo_morphology": {
        "id": "pgx:icdom-85003",
        "label": "Infiltrating duct carcinoma, NOS"
      },
      "icdo_topography": {
        "id": "pgx:icdot-C50.9",
        "label": "Breast, NOS"
      },
      "histological_diagnosis": {
        "id": "NCIT:C4017",
        "label": "Ductal Breast Carcinoma"
      }
    }
    ```

=== "Original Version 2017"


    ```json
      "bio_characteristics" : [
      {
        "description" : "breast carcinoma",
        "ontology_terms" : [
          {
            "term_id" : "NCIT:C4017",
            "term_label" : "Ductal Breast Carcinoma"
          },
          {
            "term_id" : "PGX:ICDOM:8500_3",
            "term_label" : "invasive carcinoma of no special type"
          },
          {
            "term_id" : "PGX:ICDOT:C50",
            "term_label" : "breast"
          },
        ],
      }
    ],
    ```

Additional information can be found in my recent slides for Biocuration2017 (available [through F1000](https://f1000research.com/slides/6-476) or on the [baudisgroup website](http://info.baudisgroup.org)).

Thanks especially to Paula Carrio Cordo from my group, as well as our friends and collaborators at EBI, SIB and elsewhere.

[^1]: The post has been modified somewhat to indicate the changes for current (2022) implementations (the original text has been kept as on 2017-04-13).
[^2]: Since the original post the arraymap collection has been integrated into the main [Progenetix](http://progenetix.org) site.

