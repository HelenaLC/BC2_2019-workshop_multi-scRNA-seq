# BC2_2019-workshop_multi-scRNA-seq

### Software installation

For this tutorial, you will need R 3.6, which you can download from [https://stat.ethz.ch/CRAN/](https://stat.ethz.ch/CRAN/).

We will, however, need to access the *devel* versions of various Bioconductor packages and with R 3.6, you can follow the code below (submitted to the terminal) to get a set of packages that should be compatible.  First, tell the `BiocManager` package that *devel* should be used:

```
if (!requireNamespace("BiocManager", quietly=TRUE))
    install.packages("BiocManager")

BiocManager::install(version = "devel") # will get prompted
```

For the steps below, you should be able to cut-and-paste the commands into an active session (and wait for packages and dependencies to be installed):
```
BiocManager::install("remotes")

Sys.setenv(R_REMOTES_NO_ERRORS_FROM_WARNINGS="true")
BiocManager::install("HelenaLC/muscat")

pkgs <- c("M3C","Seurat","UpSetR","cowplot",
          "msigdbr","org.Mm.eg.db","pheatmap",
          "scds","scran","topGO","ExperimentHub")
BiocManager::install(pkgs)

BiocManager::install("plger/scDblFinder")
```

### Data downloads

[TODO]
