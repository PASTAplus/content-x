# Data Exploration

At the beginning of any data reuse or synthesis project, it is important to quickly gain a thorough understanding of the type and scope of data under consideration. Additionally, it is a good practice to scan data for issues before publishing.

While data package metadata, such as the [Data Entities](/templates/resources/data-package-pages.md#data-entities) section in the full metadata page, provide concise explanations of data attributes, summary and visualization tools can provide a quick and easy interactive view into the actual data values. EDI offers three options for data exploration: Data eXplorer, Data Download Scripts, and datapie.

[TOC]

## Data eXplorer (DeX)

The EDI [Data Explorer (DeX)](http://dex.edirepository.org) is a web browser application offering summary information, subsetting, and plotting features for data packages containing tabular data files. DeX is a great tool for making a preliminary assessment about fitness for use. Click the **Data Explorer** link next to a data object from the **Resources** section of a data package landing page (currently only available in the [staging environment](/templates/resources/repository-environments.md#staging) of the Data Portal).

<img class="screen-shot" src="/static/images/dex-in-portal.png" width="80%"> 

Alternatively, open a table from a data package in DeX by providing the Data Entity URL (currently limited to tabular data). 

> In order to provide a standard of efficiency while working with limited computing power, DeX currently has a size limit of 50 million cells. Tables with more than 50 million cells will be truncated by row. For example, a table with 10 columns and 5,000,010 rows will only import the first 5,000,000 rows, leaving off the last 10 rows. The DeX profile, as well as any subsets or plots, will be generated from the truncated table and will not necessarily be representative of the original table.

### Profile

The **Profile** tab provides data table overview information, a sample of the first and last rows in the table, and summary information for every variable in the table.

#### Overview

A breakdown of dataset statistics (size, missing value and duplicate row counts, etc.) and variable types (number of datetime, numerical, unique, and other variable types). This section also includes notes for individual variables and information about the profile report.

#### Sample

This section displays the first and last ten rows of the data table, a row index, and column names.

#### Variables

For every variable in the table, this section displays a miniature summary page complete with counts of missing and duplicate rows, minimum and maximum values, and a frequency plot for the variable.

### Subset

The Subset tab allows users to filter and download data by a query, time period, row index, category, or by simply selecting the columns of interest with checkboxes.

#### Query

Users can type a query to filter data. The query syntax is based on the Python Pandas' query method.

Rows can be filtered by values in character columns using the `==` and `!=` operators:

<img class="screen-shot" src="/static/images/numexpr1.png" width="80%"> 

Rows can also be filtered by values in numeric columns using the `>`, `<`, `>=`, `<=`, `!=` and `==` operators. Use backticks to select columns that have spaces or special characters in their name:

<img class="screen-shot" src="/static/images/numexpr2.png" width="80%"> 

Rows can be filtered using comparisons between different columns. Multiple logical queries can be combined with the `&` and `|` symbols to create advanced logical queries:

<img class="screen-shot" src="/static/images/numexpr6.png" width="80%"> 

Individual rows can be selected by their index using square brackets:

<img class="screen-shot" src="/static/images/numexpr3.png" width="80%"> 

Rows where the values from two columns are equal (or not equal) may also be filtered by comparing the two columns: `col_1 == col_2` or `col_1 != col_2`

<img class="screen-shot" src="/static/images/numexpr7.png" width="120%"> 

Rows where the values from one column are present (or not present) anywhere in another column may be filtered by using the "in" (or "not in") operator with the two columns: `col_1 in col_2` or `col_1 not in col_2`

<img class="screen-shot" src="/static/images/numexpr8.png" width="120%"> 

For details, refer to the Pandas' [general guide to querying data](https://pandas.pydata.org/docs/user_guide/indexing.html#the-query-method) and the [pandas.DataFrame.query](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.query.html) API documentation specifically.

#### Time period

Users can filter by time period by selecting a **Date** column and entering a start and end date.

#### Row index

Users can filter by entering the start and end row index.

#### Category

For tables with categorical data columns declared in the EML, users can filter by specific categories within a given column.

### Plot

The **Plot** tab allows users to create scatter plots for the table by selecting an independent and one or more dependent variables.

### EML

This tab takes you back to the data package landing page.

## Data download scripts

[Data download scripts](/templates/resources/accessing-data.md#data-import-scripts), available in the **Code Generation** section of the data package landing page, read data directly from the EDI Repository into common programming language workspaces. This service provides full control over data manipulation and statistical exploration.

## datapie

The Data Package Interface for Evaluation ([datapie](https://imcr-hackathon.github.io/datapie/)) R Package lets users explore data packages that are available through the DataONE Network via an R Shiny application. _This project is under development._
