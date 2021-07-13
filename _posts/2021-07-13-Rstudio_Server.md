layout:     post
title:      "Rstudio Server"
subtitle:    "\"Cloud computing is a great euphemism for centralization of computer services under one server.\""
date:       2021-07-13
author:     "Ruby"
header-img: "/img/in-post/post-rstudio-server/rsp.png"
catalog: true
tags: 
	- 生信


## biuld R from source

大多包管理工具中的R不是最新版本。为安装特定版本（尤其是最新版本）的R，最好从source编译。

1. [流程](https://docs.rstudio.com/resources/install-r-source/)

   流程中的注意事项：

   - 安装时可能会读写系统文件，建议sudo
   - 注意自己指定的--prefix位置

2. .libPath()设置

   为使包所在的文件夹与R版本对应，并保证用户（自己）有读写权限，最好检查并自行设置libPath

- 在R内查看现有的libPaths()

  ```{r}
  .libPaths()
  ```

  想好你想用来放包的文件夹，并（创建或编辑）`~/.Renviron`文件，在其中加入：

  ` R_LIBS_SITE= %your path`

  

  ## install Rstudio Server

  [流程](https://www.rstudio.com/products/rstudio/download-server/redhat-centos/)

  ## 端口映射与运行

  1. 远程与本地端口映射：

     用localhost访问远程服务器相应端口：

     `ssh -fN -L 8787:localhost:8787 %.ssh/config中的服务器名`

  2. 运行命令：

     ```
     sudo studio-server verify-installation %无法使用时用它检查并报告错误
     
     sudo studio-server start
     
     sudo studio-server status
     
     sudo studio-server stop
     
     sudo studio-server restart
     ```

     