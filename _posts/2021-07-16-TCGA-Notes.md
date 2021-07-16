---
layout:     post
title:      "TCGA notes"
subtitle:    "\"Life isn’t about waiting for the storm to pass… It’s about learning to dance in the rain.” — Vivian Greene\""
date:       2021-07-16
author:     "Ruby"
header-img: "/img/in-post/post-rtcga-notes/lung_cancer_EM.jpeg"
catalog: true
tags: 
    - 生信
---

- 官网现成的生存曲线只针对特定的突变
- 下载病例的json文件中只有Case ID， 对应于下载数据时需要的Sample ID，需要匹配一下：
	```{r} 
	library(jsonlite)
	library(TCGAbiolinks)
	
	json <- fromJSON(paste(readLines(file),collapse=""))
	case_id <- json$submitter_id
	sample <- getResults(query, cols=c("cases"))
	case_pattern <- paste(case_id, collapse="|")
	case_sample <- sample[grepl(case_pattern), sample]
	```