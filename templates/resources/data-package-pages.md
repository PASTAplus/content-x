# Data Package Pages

A data package **[Landing Page](https://portal.edirepository.org/nis/mapbrowse?scope=edi&identifier=1)** (or **Summary Page**) and **[Full Metadata Page](https://portal.edirepository.org/nis/metadataviewer?packageid=edi.1.1)** are generated from the metadata within a data package and deliver the first impression of a data package scope and coverage to data users who are browsing on the EDI Data Portal. They can be discovered by resolving the Digital Object Identifier (DOI) of a data package, or through the Data Portal search engine. 

[TOC]

## Summary Page

The summary page displays overview information for a data package, and it can be discovered through its DOI and other links. Overview information on this page includes data package title and abstract, a list of creators, date of publication, and more explained below:

### Citation

The suggested citation for the data package and a button to copy it. For more information see  [citing a data package](/templates/resources/citing-data.md).

### Spatial Coverage

An embedded map displaying the geographic location as provided in the EML metadata. The coverage may be one or more bounding boxes, point coordinates, or a mix of both. 

### Package ID

The data package identifier. For more information see [data package identifiers](/templates/resources/the-data-package.md#identifiers-of-a-data-package).

If multiple revisions of a data package exist, this section will include links to traverse the revisions (**previous revision**, **next revision**) as well as a link to view **all revisions**.

### Resources

A list of all files associated with the data package, including the [EML file](/templates/resources/creating-metadata-for-publication.md#the-ecological-metadata-language-eml), an [Evaluation Report](/templates/resources/evaluating-a-data-package.md#interpreting-the-evaluation-report), and data entities. 

#### View Full Metadata

A link to the **Full Metadata** page.

#### View Data Package Report

A link to the [Evaluation Report](/templates/resources/evaluating-a-data-package.md#interpreting-the-evaluation-report) for the data package.


#### Download Data

A list of data entities in the data package. This section lists the entity name, file name, size, and number of downloads. The filename is linked to a direct download of the entity.


#### Download Zip Archive

This button downloads a zip file containing the data package metadata (as text and an EML file), the Evaluation Report (an XML file), a package manifest (text), and all of the data entities.

### Intellectual Rights

The license associated with the data package describing any restrictions on use. For more information see [licensing data](/templates/resources/licensing-data.md).

### Digital Object Identifier

The data package Digital Object Identifier (DOI). For more information see [data package DOIs](/templates/resources/the-data-package.md#digital-object-identifier-doi).

### PASTA Identifier

The data package [PASTA Identifier](/templates/resources/the-data-package.md#data-object-identifier).

### Code Generation

Links to generate scripts which can be run directly from local analysis software (R, Python, MATLAB, and more). These scripts enable a quick interactive view into a dataset and provide a basis for analytical workflows.

Code generation functionality is _briefly demonstrated_ in [this video](https://youtu.be/B50L1AKXcT8).

### Provenance

This section displays [provenance information](/templates/resources/provenance-metadata.md) related to the data package, including any packages that are derivations of the data package, or any data package that serve as a source to it.

<img class="screen-shot" src="/static/images/provenance-section.png" width="80%"> 

Additionally, the section contains a link to generate provenance metadata to include in derived data package metadata.


### Journal Citations

This section displays journal citations that have been added to the data package. For more information see [adding journal citations to data packages](/templates/resources/add-citation.md). 

<img class="screen-shot" src="/static/images/journal-citations-section.png" width="80%"> 

## Full Metadata Page

The **Full Metadata Page**  provides a more in-depth description of the data package. Access the full metadata page from the links at the top of the **Summary Page** and in the **Resources** section.

### General Information

The General Information section covers similar information as the top of the Summary page (title, abstract, date of publication, etc.) information that should help a data user understand the scope and coverage of the data package, as well as information about who created it or should be contacted for questions.

### Detailed Metadata

The **Detailed Metadata** section contains organized representations of almost all the elements from the EML metadata. Use the **Show** and **Hide** details buttons to expand or compact every subsection in the detailed metadata. Individual sections can be expanded or compacted using the **+/-** buttons next to the section headers.

<img class="screen-shot" src="/static/images/show-hide.png" width="80%"> 

#### Data Entities

The **Data Entities** section provides a comprehensive breakdown of each data entity (tables, spatial data, or other entities) formed from the information provided in the EML metadata. In general, the subsections underneath data entities focus on overview information (name, type, and description; number of rows and columns for tables), physical structure (size, MD5 checksum, data format), and provide a direct download link for the entity.

For **Data Tables** in particular, there is an additional subsection, **Table Column Descriptions**, that provides name, definition, data type, and more, for each individual column within the table. For columns containing numeric values, the unit and range of the column is listed. For columns containing categorical information, each code and its explanation are featured. Due to the depth of information presented in the **Table Column Descriptions** sections, data users can generally gather all the information necessary to determine a data package's fitness for their particular purpose without ever downloading a table.

### Download as XML

At the bottom of the Full Metadata Page, there is a link to download the data package's metadata as XML. This link will open the associated XML file in your browser where it can be downloaded by right-clicking and selecting **Save Page As**