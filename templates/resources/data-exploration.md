# Data Exploration

At the beginning of any data reuse or synthesis project, it is important to quickly gain a thorough understanding of the type and scope of data under consideration. Additionally, it is a good practice to scan data for issues before publishing.

While data package metadata, such as the [Data Entities](/templates/resources/data-package-pages.md#data-entities) section in the full metadata page, provide concise explanations of data attributes, summary and visualization tools can provide a quick and easy interactive view into the actual data values. EDI offers three options for data exploration: Data eXplorer, Data Download Scripts, and datapie.

[TOC]

## Data eXplorer (DeX)

The EDI [Data Explorer (DeX)](http://dex.edirepository.org) is a web browser application offering summary information, subsetting, and plotting features for data packages containing tabular data files. DeX is a great tool for making a preliminary assessment about fitness for use. Click the **Data Explorer** link next to a data object from the **Resources** section of a data package landing page.

<img class="screen-shot" src="/static/images/dex-in-portal.png" width="95%"> 

Alternatively, open a table from a data package in DeX by providing the Data Entity URL (currently limited to tabular data). 

> In order to provide a standard of efficiency while working with limited computing power, DeX currently has a size limit of 50 million cells. Tables with more than 50 million cells will be truncated by row. For example, a table with 10 columns and 5,000,010 rows will only import the first 5,000,000 rows, leaving off the last 10 rows. The DeX profile, as well as any subsets or plots, will be generated from the truncated table and will not necessarily be representative of the original table.

<div class="p-2">
  <div class="w-50 ratio ratio-16x9">
      <iframe src="https://youtube.com/embed/4ZZaLQ72GPc" title="YouTube video" allowfullscreen=""></iframe>
  </div>
</div>


## Data download scripts

[Data download scripts](/templates/resources/accessing-data.md#data-import-scripts), available in the **Code Generation** section of the data package landing page, read data directly from the EDI Repository into common programming language workspaces. This service provides full control over data manipulation and statistical exploration.

## datapie

The Data Package Interface for Evaluation ([datapie](https://imcr-hackathon.github.io/datapie/)) R Package lets users explore data packages that are available through the DataONE Network via an R Shiny application. _This project is under development._
