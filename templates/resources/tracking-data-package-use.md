# Tracking Data Package Use

Metrics of activity surrounding a data package are commonly used when publicizing a data publication or reporting to funders.

[TOC]

## EDI Package Tracker

[The Package Tracker](https://dashboard.edirepository.org/dashboard/reports/package_tracker), a feature of the EDI Dashboard, is a convenient tool for viewing the resources and downloads of a given data package. For more information see [the EDI Dashboard](/templates/resources/the-edi-dashboard.md).

<img class="screen-shot" src="/static/images/package-tracker.png" width="25%">


## Data package summary page

Each data package [landing page](/templates/resources/data-package-pages.md) provides activity information in multiple places. The **Resources** section has the number of views the metadata has received, and the number of downloads for each resource. The **Provenance** and **Journal Citations** sections, as well as the **DataCite** Badge at the bottom of the summary page, all provide information on where a data package has been used or cited.


## EDIutils

Using the functions provided by the [EDIutils](https://ediorg.github.io/EDIutils/) R Package, it is possible to easily retrieve download and citation metrics for a data package. These processes have been detailed in [Retrieve Download Metrics](https://ediorg.github.io/EDIutils/articles/retrieve_downloads.html) and [Retrieve Citation Metrics](https://ediorg.github.io/EDIutils/articles/retrieve_citations.html) vignettes that accompany the package.

For a language agnostic solution follow a similar process using the [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html) documentation.
