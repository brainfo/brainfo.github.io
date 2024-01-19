---
layout:     post
title:      "Python on HPC"
date:       2023-06-02
author:     "Ruby"
header-img: "img/in-post/post-python-hpc/node.png"
disqus_username: brainfo
catalog: true
tags:
    - bioinformatics
    - computing
    - python
    - hpc
    - server
---
## Q & A
1. is it recommended to use jupyter on bianca?

   > Yes, you may.

   > Use Thinlinc then!
   
2. For all the python scripts as in the examples/progams, we need to submit them with slurm on uppmax or hpc2n?

   > The examples we have are all small, in principle you would not need to submit them to Slurm, but in general it is good to either sumit your jobs to Slurm or start an interactive session and run the scripts that way. In the afternoon we’ll be using the GPU nodes. Those jobs cannot be run on the login nodes.

3. For the python packages preinstalled and need to be loaded, are we assured that the version is compatible if we already load the python before loading the python packages. Or could we specify or must we specify the version for the packages also. Does this also fit for modules outside python? Is it assured and safe guard of the version conflict?

   > When you load the python module, there are a set of pip packages available which are compatible with that particular python version. You can check what those packages are with pip list. If you need a different version of those packages, or additional packages, I would reccoment you do that in a separate environment. That way you may specify which specific version of a package you need.

4. Do we have a shared base env for the venvs?

    > nope

5. So how to run jupyter on computing node

    > Guide at HPC2N: https://www.hpc2n.umu.se/resources/software/jupyter

    > Guide at UPPMAX: https://www.uppmax.uu.se/support/user-guides/python-user-guide/#tocjump_35143811955682613_13

    > https://hackmd.io/@pmitev/UPPMAX-jupyter

6.  Does it matter with the order of the ml modules and the source venv?

    > With source <environment>/bin/activate, ml python/X won’t be necessary

    comment: the python in the environment is from the previous module load python, and it’s kept in.

    > This also holds true for virtualenv

    > You can prove this by doing which python in the environment. It will point to <environment>/bin/python.

    > python -V will be the version of python you loaded when you CREATED the virtual environment

7. On rackham it’s quite direct to use vs code remote server, but if it’s possible on bianca? I even never successfully set the ssh-key there.

    > Bianca is not possible as far as I know

    > Although there is a VSCodium module that can be run on-site on bianca, I believe.

8.  There's time limit for interactive allocation?

    > Same as for batch

    > But recognize that devcore and devel partitions are maximum --t 1:0:0