# Adding Journal Citations to a Data Package

Adding journal citations to a data package allows authors to measure the impact that their data are making and allows potential users to see the context in which the data have been previously applied.

While EDI takes measures to cross reference new articles to cited data packages, occasionally one is missed. When this is the case, journal citations can be added by emailing the EDI Curation Team with the required information or directly by anyone with an EDI account via the EDI Data Portal, the EDIutils R Package, or the REST API.

>The term "journal citations" is broadly defined and includes any external media in which the data have been cited (e.g. reports, articles, software, etc.).

[TOC]

## Required information

A journal citation must contain a [data package identifier](the-data-package.md#data-package-identifier), an article identifier (either a DOI or URL), and a description of the relationship between the article and data package. Including the title of the article and journal is recommended.

### Relation types

The relation between a journal citation and data package must be described when linking a journal citation. There are three types of relations between data packages and journal articles [provided by DataCite](https://support.datacite.org/docs/relationtype_for_citation) and supported by EDI:

#### IsCitedBy

* The data package is formally cited in the article.
* The data package is explicitly cited within the article. 
* The data package DOI, a longform citation, or any other indicator identifies a specific data package in the journal article (as data availability statement, in the acknowledgements, methods, citation sections, or supplemental materials).

#### IsDescribedBy

* The data package is explicitly described within the article.
* Journal articles that explicitly describe the data package, such as a [data paper](https://esajournals.onlinelibrary.wiley.com/hub/journal/19399170/resources/data_paper_inst_ecy).

#### IsReferencedBy

* The data package is implicitly described within the article.
* The data package was used to produce the results presented in the article but the data package DOI or a longform citation is not present in the article.
* A knowledgeable person assures the use of this data package in the article. 
* When linking an older journal article to a newly published data package.

## Adding a citation to a data package

### EDI Data Portal

Journal citations can be added to data packages manually from the [EDI Data Portal](https://portal.edirepository.org/nis/home.jsp):

1. Access the **Journal Citations** tool from the dropdown navigation menu

<img src="/static/images/journal-citation-tools-dropdown.png" width="75%">

or from the **Add Journal Citation** button at the bottom of a data packages landing page

<img src="/static/images/journal-citations-landing.png" width="75%">

2. Add the citation information, then use the **Add Journal Citation** button to create and add the journal citation. 
3. Journal citations can also be updated or deleted using the journal citation tool.

<img src="/static/images/journal-citation-tool.png" width="75%">

[Watch a video walkthrough](https://www.youtube.com/watch?v=XyyrH4EzTNc&t=291s) demonstrating the use of the journal citation tool.


### EDIutils

Journal citations can be added to data packages programmatically with the [EDIutils R package](https://ediorg.github.io/EDIutils/). Provide the required and optional citation information as arguments to the [`create_journal_citation()`](https://ediorg.github.io/EDIutils/reference/create_journal_citation.html) function.

For a language-agnostic solution, see the REST API documentation for [Create Journal Citation](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#create-journal-citation).
