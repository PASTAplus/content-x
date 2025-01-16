# Designing a Data Package

When designing a [data package](/templates/resources/the-data-package.md), it is important to consider multiple factors in order to satisfy local or community research needs. Considerations such as whether data should be published as a single package or in a set of related packages must be made to ultimately create a data package that is optimized for discovery and reuse.

[TOC]

## Considerations for design

### Reproducible science

If publishing data in support of a manuscript, then include the data and processing scripts required to reproduce the results.

<img src="/static/images/reproducible-research.png" width="15%"> 

### Duplicated data

Have these exact data been published elsewhere? If so, then don't republish unless [the duplication is warranted](https://ediorg.github.io/data-package-best-practices/guide-special-cases/other-repositories.html). Duplicates create maintenance issues for data managers and confusion for users. If data published elsewhere is used to create a derived dataset, reference these data via [provenance metadata](/templates/resources/provenance-metadata.md). Derived data are not exact copies and can be archived. Mutable data licensed under the public domain can be archived. When in doubt, consult the data authors before republishing.

<img src="/static/images/organize-duplication.png" width="25%"> 

### Theme of the data

Data packages may include the full set of data for one study, or each type of measurement (e.g. biological, chemical, physical) may comprise its own data package. The decision depends on the research question from the study, and whether all data are needed to interpret them or if they may be used out of context from each other.

<img src="/static/images/organize-theme.png" width="25%"> 

### Method of collection

In long-term observations, sampling methods may change. This may warrant separating the data into different data packages to account for altered accuracy, precision, and other attributes. Clear communication of changes or the relationship between data packages is important. 

<img src="/static/images/organize-methodology.png" width="25%"> 

### Location of collection

Similar considerations apply to sampling location. Grouping by location can either improve discovery of related data or "clutter" organization and understanding.

<img src="/static/images/organize-location.png" width="25%"> 

### Completeness of the data

Some "ancillary" or background data or information may be critical in understanding and interpreting the collected data. 

<img src="/static/images/organize-relation.png" width="75%"> 

### Size of data files

Size is important for up- and download. Consider breaking the data up into smaller manageable units. There is a soft limit of 500 MB when uploading via the EDI Data Portal (which can be avoided by data managers with an EDI account and [uploading with static data links](/templates/resources/uploading-with-static-data-links.md)), and a hard limit of 100 GB. Please [contact us](/templates/support/contact-us.md) if your data publication will exceed either of these limits and we will help you find a solution.

<img src="/static/images/organize-volume.png" width="25%"> 

### Sampling frequency

For data collected at high sampling frequencies, consider providing down-sampled versions of the data to accommodate users preferring a coarser temporal grain. Different temporal frequencies should be separated into different data objects but included in the same package for ease of discovery.

<img src="/static/images/organize-frequency.png" width="45%"> 

### Level of processing

Always try to archive the "minimally processed" version of the data so future users can apply methods appropriate to their research. However, if a lot of effort has gone into formatting and cleaning data, those should be published as well, either in the same package or separately with [provenance metadata](/templates/resources/provenance-metadata.md) to make the relationship clear between them.

<img src="/static/images/data-processing-levels.png" width="90%"> 
