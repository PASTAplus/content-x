# Thematic Standardization

Data in the EDI Repository are thematically and structurally diverse. Converting them into standardized formats, according to theme, facilitates interoperability and reuse. 

Thematic standardization is a cooperative effort to develop and support a design pattern which serves as a standardized intermediary between raw "Level-0" data and synthesis research "Level-2" data. Collaborative effort to build tools that support the creation and use of the intermediate "Level-1" datasets, helps to incentivize the extra effort of reformatting and increase the likelihood of data reuse.

<img src="/static/images/thematic-standardization-workflow.png" width="90%">

EDI currently has two thematic standardization projects: ecocomDP and hymetDP.

[TOC]


## ecocomDP

ecocomDP is a dataset design pattern and R package for ecological community data. The motivation and effort that led to its creation is documented in [O'Brien et al. 2021](https://doi.org/10.1016/j.ecoinf.2021.101374). Details on creating and using ecocomDP datasets can be found on the [ecocomDP R package webpage](https://ediorg.github.io/ecocomDP/). EDI is also creating a L2 data product from L1 ecocomDP data: a Darwin Core Archive suitable for contribution to GBIF.

## hymetDP

hymetDP is a dataset design pattern and R package for hydrological and meteorological data. The design pattern is based on the CUAHSI Community Observations Data Model Version 1.1 [design specifications](https://his.cuahsi.org/documents/odm1.1designspecifications.pdf). The R package, which is [under development](https://github.com/kzollove/hymetDP), is largely based off of the framework laid out by the ecocomDP project.

## Discovering thematic standardization data

### EDI Data Portal

Data packages from thematic standardization projects can be discovered from the EDI Data Portal Search Engine through the [Advanced Search](https://portal.edirepository.org/nis/advancedSearch.jsp) interface. From the **Subject** tab, select the **Keywords only** radio button, and search for the name of the data pattern (i.e. "ecocomDP", "hymetDP"). Thematic Standardization data packages will always have the name of their design pattern as a keyword, which allows this type of searching.

<img class="screen-shot" src="/static/images/keyword-search.png" width="100%">

>A similar keyword search can be used to discover Darwin Core versions of the ecocomDP data packages. Instead of the name of the data pattern, search for "Darwin Core Archive (DwC-A) Event Core" (including the double quotes).


### R Packages

The [ecocomDP](https://cran.r-project.org/web/packages/ecocomDP/index.html) and [hymetDP](https://github.com/kzollove/hymetDP) R packages have a built-in function, `search_data()`, to search across an index of existing standardized data packages from within an R environment.
