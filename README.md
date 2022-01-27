Bioconductor on Microsoft Azure
=====================================================

[Nitesh Turaga](https://www.linkedin.com/in/niteshturaga/); Erdal Cosgun; and Vince Carey

Teaser: Using Bioconductor on Microsoft Azure cloud resources for scalable genomic computing.

## Introduction

The [Bioconductor project](https://bioconductor.org) promotes the statistical analysis and
comprehension of current and emerging high-throughput biological
assays. Bioconductor is a strict proponent to open source and open
development of software; and collaborative, literate, and reproducible
research.

As the scale of genomic data grows exponentially in the genomics era,
the use of cloud services is on the upward trend to deal with the size
of the data. The advantage of cloud computing services fits the needs
of the analysis of the varying size of data depending on the analysis
setting. The **elasticity** and **scalability** of cloud services is a
resource that makes it easy for a small lab or a large company to take
advantage of Bioconductor's open source software, and data resources.

![Bioconductor website](https://github.com/nturaga/bioc_msr_tech_blog/blob/master/bioconductor-website.png)

## Bioconductor Docker Images

Bioconductor produces docker images so that users can run the latest
stable version of R, Bioconductor using either the command line or an
RStudio UI. These images are built with system libraries that can be
used to install (and compile) over 2000 Bioconductor packages.

These docker images hosted by Bioconductor are available on the
Microsoft container registry (MCR) and are freely available to the
public on an open-source Artistic-2.0 license.

```
docker pull mcr.microsoft.com/bioconductor/bioconductor_docker:RELEASE_3_14
```

These images can be used with Azure container instances (ACI) with the available [launch instructions](http://bioconductor.org/help/docker/#msft).

The added benefit of these docker images are the availability of
pre-compiled Bioconductor package binaries. These package binaries
speed up the installtion of packages on the Docker image and provide
users an efficient reasearch computing environment where exploratory
data analysis is faster.

Since this is a more recent feature in development - it is available
on a branch of the CRAN package `BiocManager` that will be merged
soon. An example of installation of binary packages is given below:

```{r}
BiocManager::install('Bioconductor/BiocManager@anvil')

pkgs <- c('BiocParallel', 'rsbml', 'rhdf5`)

BiocManager::install(pkgs)
```

## Bioconductor Hubs - AnnotationHub and ExperimentHub data

Bioconductor distributes it's annotation and experiment hub data
through Azure Storage containers. The Bioconductr

AnnotationHub resource provides a central location where genomic
files (e.g., VCF, bed, wig) and other resources from standard
locations (e.g., UCSC, Ensembl) can be discovered. The resource
includes metadata about each resource, e.g., a textual description,
tags, and date of modification.

ExperimentHub provides a central location where curated data from
experiments, publications or training courses can be accessed. Each
resource has associated metadata, tags and date of modification.

As of this post, (1/27/2022) about **2.5 TB** of data has been distributed
to important genomic research to scientists around the world.

![BioconductorHubs Usage Stats for 1 month](https://github.com/nturaga/bioc_msr_tech_blog/blob/master/BioconductorHubs-Egress.png)


The Genomics Data Lake provides various public datasets that you can access for free and integrate into your genomics analysis workflows and applications. The datasets include genome sequences, variant info, and subject/sample metadata in BAM, FASTA, VCF, CSV file formats. The Genomics Data Lake is hosted in the West US 2 and West Central US Azure region. Allocating compute resources in West US 2 and West Central US is recommended for affinity. The Bioconductor Annotation and Experiment Hub data will be available on [Microsoft Genomic Data Lake](https://docs.microsoft.com/en-us/azure/open-datasets/dataset-genomics-data-lake) on mid-February 2022.

You can find the sample Jupyter notebooks from this [repo](https://github.com/microsoft/genomicsnotebook) to download the Genomics Data Lake's data on your R-Bioconductor project. Another useful way to use Bioconductor packages on Azure is to use built-in Genomics Data Science VMs on Azure. You can easily deploy your Windows OR Linux VMs from this [link.](https://github.com/microsoft/genomicsnotebook/tree/main/genomics-data-science-vm)

## Future developments

OSCA book - docker image for OSCA book

Binary production on AKS with BiocKubeInstall

Azure utils for AnVIL package

