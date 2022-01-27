Bioconductor and its applications in Microsoft Azure
=================

Authors: Nitesh Turaga (nitesh@ds.dfci.harvard.edu); Erdal Cogsun; and Vince Carey


1. Overview.

3. Bioconductor docker image availability on Microsoft container registry.

5. OSCA book on Azure - how we solve binaries issue here. (! big one)

6. Annotation and Experiment Hubs on Azure Storage containers.

4. Building and distributing binaries for faster installation of packages.

7. Future developments

## Overview

The Bioconductor project promotes the statistical analysis and
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

## Bioconductor Hubs - Annotation and Experiment data

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

As of this post, (1/27/2022) about 2.5 TB of data has been distributed
to important genomic research to scientists around the world.

< INSERT correct link here>
The Bioconductor Annotation and Experiment Hub data details can be
found on [Microsoft Genomic Data
Lake](https://docs.microsoft.com/en-us/azure/open-datasets/dataset-genomics-data-lake).

![images/BioconductorHubs-Egress.png](BioconductorHubs-Egress)


## Future developments
