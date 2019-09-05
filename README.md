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

For the pratical part of the workshop, we will be analyzing a replicated two-condition dataset of brain cortex tissue from mice treated with lipopolysaccharide (LPS), which is available [HERE](http://imlspenticton.uzh.ch/teaching/BC2_2019-workshop_multi-scRNA-seq).

* **1-SCE_reduced.rds**: `SingleCellExperiment` (SCE) subset of the LPS dataset from Crowell *et al.*<sup>[1](#f1)</sup>
* **2-SO_integrated.rds**: `SeuratObject` obtained after preprocessing & integration
* **3-SCE_clustered.rds**: final clustered & annotated SCE for downstream analyses

<a name="f1">[1]</a>: 
Crowell HL, Soneson C\*, Germain P-L\*,  
Calini D, Collin L, Raposo C, Malhotra D & Robinson MD:  
On the discovery of population-specific state transitions from  
multi-sample multi-condition single-cell RNA sequencing data.  
*bioRxiv* **713412** (July, 2019). doi: [10.1101/713412](https://doi.org/10.1101/713412)