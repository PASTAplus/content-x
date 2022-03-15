# Provenance Metadata

Provenance is the origin or history of data and is an important piece of metadata to make research transparent and reproducible. Several elements in metadata are involved in documenting data provenance. First and foremost is a detailed description of the methods by which the data were collected and created. Data processing scripts (R, Python, etc.) provide very detailed provenance information and can be published in a data package. For the special case of a derived dataset, i.e. data that is compiled from one or more other 'original' datasets, a detailed list of those original datasets should be included. Listing such datasets will give the original data creator proper credit, even when more datasets are used than can reasonably be cited in a resulting paper.

<img src="/static/images/provenance.png" width="15%">

[TOC]

## Creating provenance metadata

Provenance metadata for data sources both internal and external to the EDI Data Repository can be created using ezEML and EMLassemblyline. The EDI Data Portal and EDIutils only support the creation of metadata only internal to the EDI Repository.

### ezEML

To create provenance metadata using [ezEML](https://ezeml.edirepository.org/eml/):

1. From the **Methods** tab, click the **Add Method Step** button. 
2. In the **Data Sources** textbox, enter as much information about the source dataset(s) as possible. At minimum, provide the DOI or a URL linking to the data source. The name and email for the data creator and contact are valuable information that should be provided, if available.
3. Click **Save and Continue**

>Provenance metadata submitted via ezEML is converted by data curators to the EML formatted provenance &lt;methodStep> before publishing in the EDI Data Repository. Data curators processing an ezEML submission should see the EDI Data Portal section below for an example of the EML provenance format.


### EMLassemblyline

To create provenance metadata using [EMLassemblyline](https://ediorg.github.io/EMLassemblyline/):

1. Run the [`template_provenance()`](https://ediorg.github.io/EMLassemblyline/reference/template_provenance.html) function to create an empty provenance template.
2. For data sources originating from the EDI Data Repository, populate the template **dataPackageID** field with the EDI [data package identifier](the-data-package.md#data-package-identifier) and specify "EDI" in the **systemID** field. Use the other fields of this template when creating provenance for data sources external to EDI Repository.
3. Run the [`make_eml()`](https://ediorg.github.io/EMLassemblyline/reference/make_eml.html) function to add the provenance metadata to the EML for the derived data.

### EDI Data Portal

To create provenance metadata from the [EDI Data Portal](https://portal.edirepository.org/nis/home.jsp):

1. Navigate to the **Provenance** section at the bottom of a data package [landing page](data-package-pages.md). This section displays provenance information and includes a link to generate provenance metadata for the data package.

<img src="/static/images/provenance-portal2.png" width="85%">

2. This links to the **Provenance Generator**. The **Provenance Metadata XML** tab contains text for the &lt;methodStep> element. Copy the entire &lt;methodStep> element.

<img src="/static/images/provenance-generator.png" width="85%">

3. Open the EML for the derived data package in an XML editor and navigate to the &lt;methods> element. 
4. Paste the copied provenance &lt;methodStep> element at the end of the list of &lt;methodSteps>. Repeat for all data sources.

See [Editing EML](https://docs.google.com/document/d/12sdLhID6SwaKAjU1aT5PAXA-9q1zaq31eNBmPRvYBC0/edit#heading=h.j5rijoovspu3) for more on XML editors.

### EDIutils

To create provenance metadata from the [EDIutils](https://ediorg.github.io/EDIutils/) R Package:

1. Run the [`get_provenance_metadata()`](https://ediorg.github.io/EDIutils/reference/get_provenance_metadata.html) function with the corresponding source [data package identifier](the-data-package.md#data-package-identifier).
2. Add the returned &lt;methodStep> element into an EML R object of a derived data package or write it to file for other use cases.

For a language-agnostic solution, see the REST API documentation for [Get Provenance Metadata](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#get-provenance-metadata).

## Resources

* [End-to-End Provenance](https://github.com/End-to-end-provenance/End-to-end-provenance.github.io/blob/master/README.md) - Software tools to collect and use provenance information.
