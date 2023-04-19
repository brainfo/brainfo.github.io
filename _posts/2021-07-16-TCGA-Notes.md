---
layout:     post
title:      "TCGA notes"
subtitle:    "\"Life isn’t about waiting for the storm to pass… It’s about learning to dance in the rain.” — Vivian Greene\""
date:       2021-07-16
author:     "Ruby"
header-img: "/img/in-post/post-rtcga-notes/lung_cancer_EM.jpeg"
catalog: true
disqus_username: brainfo
tags: 
    - 生信
---

## 检索

检索数据的一般过程是，选择自己感兴趣的突变并为止建立突变集、选择自己感兴趣的病例并建立病例集。突变集和突变集、病例集和病例集可以做并和异或的操作。
然后就可以根据病例集和突变集的积选择符合突变要求的病例了。对于这些感兴趣的病例，可下载病例及注释信息的json文件（网站提供的文件中json文件最全面）。

## 简单分析注意事项
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