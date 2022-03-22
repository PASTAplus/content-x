# Accessing Data

Data packages and their contents can be accessed through the EDI Data Portal, EDIutils R Package, and the REST API. These options support scientific workflows driven by manual human effort and automated machine routines.

<img src="/static/images/access.png" width="30%">

[TOC]

## Data Portal

The [EDI Data Portal](https://portal.edirepository.org/nis/home.jsp) provides data access through a user-friendly web browser interface.

### Point and click

Single data objects or the entire data package can be downloaded as files:

1. From a [data package landing page](/templates/resources/data-package-pages.md), navigate to the **Resources** section:

<img src="/static/images/access-resources.png" width="65%">

2. Download individual resources by clicking the links under **Download Data**.
3. Use the **Download Zip Archive** button to download the entire data package.

### Data import scripts

Data import scripts, read data directly from the EDI Repository into common programming language workspaces. This option supports reproducible research by accessing the data directly and reducing the possibility of errors propagating through local files.

1. Navigate to the **Code Generation** section of a data package landing page. 
2. Select the language of interest (R, Python, MATLAB, etc).
3. Download the script that is generated as a file, or copy and paste the text into the development environment of the language (e.g. RStudio).

## EDIutils

The [EDIutils R package](https://ediorg.github.io/EDIutils/) allows data to be read directly from the EDI Repository into the R environment. This option serves a similar use case as the data import scripts but provides full access to the [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html), which is useful when constructing automated workflows.

1. Download the metadata of a data package using the [`read_metadata()`](https://ediorg.github.io/EDIutils/reference/read_metadata.html) function.
2. Download individual resources from a data package using the [`read_data_entity()`](https://ediorg.github.io/EDIutils/reference/read_data_entity.html) function.
3. Download an entire data package as a zip archive using the [`create_data_package_archive()`](https://ediorg.github.io/EDIutils/reference/create_data_package_archive.html) and [`read_data_package_archive()`](https://ediorg.github.io/EDIutils/reference/read_data_package_archive.html) functions.

See the [Search and Access Data vignette](https://ediorg.github.io/EDIutils/articles/search_and_access.html) for examples.

For a language-agnostic solution, see the REST API documentation on [Read Metadata](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#read-metadata), [Read Data Entity](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#read-data-entity), [Create Data Package Archive](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#create-data-package-archive), and [Read Data Package Archive](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#read-data-package-archive-1).


## Accessing embargoed data

Embargoed data can be accessed by users who are authorized according to the &lt;access> element of the EML file. Users should reach out directly to the contact listed on the data package for access to embargoed data. If the contact is unresponsive, [contact EDI](/templates/support/contact-us.md) for assistance.
