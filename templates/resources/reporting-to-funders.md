# Reporting to Funders

Research funders often require project data to be archived in a trustworthy repository for future discovery and use. EDI provides services for projects to generate a list of associated data publications and provide metrics on the reuse and impact.

[TOC]

## Listing data publications

A list of recent publications from a research project/site and a full list of publications can be generated with the [Upload Report](/templates/resources/the-edi-dashboard.md#upload-report) and [Site Report](/templates/resources/the-edi-dashboard.md#site-report) services, respectively. Currently, these services are only available to LTER projects but will be updated to support all projects/sites in the future. In the meantime, generating a list of data publications requires navigating to each [data package landing page](/templates/resources/data-package-pages.md) and copying the relevant information into the body of a report.

## Impact of data publications

See [Tracking Data Package Use](/templates/resources/tracking-data-package-use.md) for services related to listing the views, downloads, and citations of published data packages.

## EDIutils

Using the functions provided by the [EDIutils](https://docs.ropensci.org/EDIutils/index.html) R Package, it is possible to easily retrieve download and citation metrics for a data package. These processes have been detailed in [Retrieve Download Metrics](https://docs.ropensci.org/EDIutils/articles/retrieve_downloads.html) and [Retrieve Citation Metrics](https://docs.ropensci.org/EDIutils/articles/retrieve_citations.html) vignettes that accompany the package.

For a language agnostic solution follow a similar process using the [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html) documentation.

## Reporting to NSF

NSF recently opened its [Public Access Repository](https://par.nsf.gov/) for data. Once logged in to **[research.gov](https://www.research.gov/research-web/) / Awards and reporting / Add Research Product**, it is possible to enter an EDI data package DOI and the full citation information will be filled in automatically. The record may then be linked to an award in the NSF system to which the logged in person has access.

Alternatively, data packages may be included in BibTex files as **Other Publication** and uploaded in the products section of an annual report.
