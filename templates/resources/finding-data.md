# Finding Data (Search Engines)

Finding data of interest is an important first step in data reuse. Recognizing this, EDI takes extra effort to expand data discovery beyond the EDI Search Engine to also include the DataONE and Google Dataset Search Engines.

[TOC]

## EDI Search Engine

Searchable components of data package metadata are indexed by the EDI Search Engine. The [full set of searchable fields](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#searchable-fields) are listed in tabs of the EDI Data Portal [Advanced Search Interface](https://portal.edirepository.org/nis/advancedSearch.jsp).


### EDI Data Portal

Simple text search and the advanced search interface are accessible from the [EDI Data Portal home page](https://portal.edirepository.org/nis/home.jsp).

<img class="screen-shot" src="/static/images/search1.png" width="90%">

#### Advanced search

The advanced search interface consists of eight feature tabs, each representing a different search parameter. These search parameters can be used individually or in tandem with the others to create a query with which to search for datasets. When using the advanced search interface, any selected parameters will be saved until the **Submit** button is pressed. All parameters are combined with a boolean "AND". After pressing submit, use the web browser back button to refine search parameters. To reset all parameters, click the **Clear All** button.

> Overly specific search criteria may result in poor search results dataset? If this is the case, try reducing the search criteria.

##### Spatial / Place Name

Search by the name of a location or set geographic boundaries from the **Spatial / Place Name** tab. Geographic boundaries can be set by zooming in on a map or by entering coordinates and selecting **Dataset is Contained within Boundaries**.

<img class="screen-shot" src="/static/images/as-spatial.png" width="95%">

##### Sites

Find data from a subset of LTER sites from the **Sites** tab. Hold the shift button to highlight consecutive site names, or the control/command button to select multiple disparate sites.

<img class="screen-shot" src="/static/images/as-sites.png" width="95%">

##### Subject

Add a text search to your query from the **Subject** tab. Text search can be applied specifically to the metadata title, abstract, or keywords (or all three) using the radio buttons. The search can be expanded by allowing the query to return results that include more specific terms (a search for "aquatic" would include "lakes"), related terms (a search for "lakes" would include "ponds"), or both. Expand the search even further by including the 15403 data packages from the [EcoTrends](https://lternet.edu/the-ecotrends-project/) and 10492 data packages from the [LTER Landsat](https://lternet.edu/lter-remote-sensing-and-geographic-information-system-data/) projects in the results. 

<img class="screen-shot" src="/static/images/as-subject.png" width="95%">

##### Creator / Organization

To limit search results to a specific creator or organization, select names from the dropdown lists under the **Creator / Organization** tab.

<img class="screen-shot" src="/static/images/as-creator.png" width="95%">

##### Temporal

From the **Temporal** tab, narrow the query to specific dates of data collection or publication with the **Start Date** and **End Date**. Search for studies that cover specific durations with **Min Duration** and **Max Duration**. Narrow results to specific time periods with **Named Time-Scale**.

<img class="screen-shot" src="/static/images/as-temporal.png" width="95%">

##### Taxonomic

Filter on a specific taxon in the **Taxonomic** search tab.

<img class="screen-shot" src="/static/images/as-taxonomic.png" width="95%">

> Warning: Not many datasets have taxonomic metadata for the search engine to operate on. This search feature will become more useful as data packages include this taxonomic information.

##### Project

Use a project title or a funding ID to narrow results from the **Project** tab.

<img class="screen-shot" src="/static/images/as-project.png" width="95%">

##### Identifier

Search for a specific package identifier from the **Identifier** tab. 

<img class="screen-shot" src="/static/images/as-identifier.png" width="95%">

### EDIutils

The [`search_data_packages()`](https://ediorg.github.io/EDIutils/reference/search_data_packages.html) function allows programmatic search across the EDI Data Repository using [Apache Solr queries](https://cwiki.apache.org/confluence/display/solr/). See the [Search and Access vignette](https://ediorg.github.io/EDIutils/articles/search_and_access.html) for an example of searching and accessing data using EDIutils.

For a language-agnostic solution, see the REST API documentation for [Search Data Packages](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#search-data-packages).

## DataONE Search Engine

The [DataONE Search Engine](https://search.dataone.org/data) allows data users to search for EDI data packages alongside other member repositories specializing in Ecological, Earth, and Environmental research. Along with some search parameters similar to those offered by EDI, users can search across a subset of **Member Nodes** (i.e. data repositories), and filter datasets that contain specific data attribute types (i.e. measurement variables) or by embedded keyword tags. 

<img class="screen-shot" src="/static/images/dataone-search.png" width="100%">

## Google Dataset Search Engine

The [Google Dataset Search Engine](https://datasetsearch.research.google.com/) facilitates discovery of EDI data among all datasets on the internet. Currently, the search accepts queries in a free text form and search results can be filtered by last updated, download format, usage rights, and topic.

 
