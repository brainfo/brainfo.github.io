---
layout:     post
title:      "Bioinformatics Databases"
subtitle:   " \"Information is not knowledge, and knowledge is not wisdom.\""
date:       2023-03-05
author:     "Ruby"
header-img: "/_posts/img/in-post/post-databases/databases.jpg"
catalog: true
tags:
    - bioinformatics
---
![test](/_posts/img/in-post/post-databases/databases.jpg)
## Gene ontology and network
1. [GeneMania](https://genemania.org/): for beautiful gene networks. Indexing 2830 association networks containing 60554667 interactions mapped to 166691 genes from 9 organisms.  
   ![Input *Ar* and Mouse as an example](/_posts/img/in-post/post-databases/GeneMania_example.png)  
   [Usage case in peer reviewed paper](https://www.pnas.org/doi/abs/10.1073/pnas.1722617115?url_ver=Z39.88-2003&rfr_id=ori:rid:crossref.org&rfr_dat=cr_pub%20%200pubmed)
2. [Pathway Commons](http://www.pathwaycommons.org/)  
   ![Androgen receptor](/_posts/img/in-post/post-databases/AndrogenReceptor.png)
3. [Human transduct signaling pathways](http://netpath.org/pathways?path_id=NetPath_2)  
   ![Androgen receptor signaling pathway](/_posts/img/in-post/post-databases/NetPath_example.png)
4. [Mouse knowledgebase](https://www.informatics.jax.org/): Genes (ontology and signaling pathways), phenotypes & mutant alleles, Human-Mouse disease connection, gene expression, cre, strains & polymorphisms, homology, cancer models, ... 
5. [Enrichr](https://maayanlab.cloud/Enrichr/)
   [Usage case in peer reviewed paper](https://www.cell.com/cell/pdf/S0092-8674(22)00070-8.pdf)
   
## TF regulon
[Encode transcription factor targets](https://maayanlab.cloud/Harmonizome/dataset/ENCODE+Transcription+Factor+Targets): 22449 genes, 181 TFs and 1651393 gene transcription factor associations by binding of transcription factor near transcription start site of gene 

## Gene expression
1. Tissue level: 
   1. BioGPS provides an extensive annotation using gene expression from ArrayExpress, Exon array Gene Atlas, Gene expression/activity chart, Gene Expression Atlas (ArrayExpress Atlas), NCBI Gene Expression Nervous System Atlas (GENSAT), The Human Protein Atlas and a 15 human placenta studies.  
   2. ARCHS4 provides access to gene counts from HiSeq 2000 and HiSeq 2500 platforms from GEO and Sequence Read Archive (SRA).

## Cell type markers:
   1. [Cell Ontology](https://obofoundry.org/ontology/cl.html). CL was first developed as a platform in 2004 to collect major cell types from humans and model organisms, and has since been applied to various fields. Each CL has a permanent url.
   2. Panglaodb provides 13 marker genes for undefined human placental cells identified from embryonic and placental tissues without distinguishing cell types. 
   3. CellMarker provides marker genes for 17 cell types from human placenta tissues from either single-cell sequencing, experiment, or review, are reported. 
   4. Human protein atlas reanalyzed the first-trimester human fetal interface single-cell transcriptomic data from Vento-Tormo, et al. altogether with data from 36 other tissues. They identified 3 cell type enriched genes in cytotrophoblasts, 45 in syncytiotrophoblasts, and 26 in extravillous trophoblasts via the elevated mRNA level compared to other cell types.
   5. [Descartes cell atlas](https://descartes.brotmanbaty.org/bbi/human-gene-expression-during-development/) depositing data from a peer reviewed papar.
   6. The Human BioMolecular Atlas Program (HuBMAP) ASCTplusB tables include information about full-term human placenta. For this database, protein and lipid biomarkers have been curated for 24 cell types based on published placental histopathologic nomenclature, and literature on cell-type specific biomarkers.
   7. Celltypist, especially for immune cells.
   
## genome browser
I like [WashU](http://epigenomegateway.wustl.edu/)