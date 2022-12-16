# Provenance Metadata

Provenance is the origin or history of data and is an important piece of metadata to make research transparent and reproducible. Several elements in metadata are involved in documenting data provenance. First and foremost is a detailed description of the methods by which the data were collected and created. Data processing scripts (R, Python, etc.) provide very detailed provenance information and can be published in a data package. For the special case of a derived dataset, i.e. data that is compiled from one or more other 'original' datasets, a detailed list of those original datasets should be included. Listing such datasets will give the original data creator proper credit, even when more datasets are used than can reasonably be cited in a resulting paper.

<img src="/static/images/provenance.png" width="15%">

[TOC]

## Creating provenance metadata

Provenance metadata for data sources both internal and external to the EDI Data Repository can be created using ezEML and EMLassemblyline. The EDI Data Portal and EDIutils only support the creation of metadata internal to the EDI Repository.

### ezEML

To create provenance metadata using [ezEML](https://ezeml.edirepository.org/eml/):

1. From the **Methods** tab, click the **Add Method Step** button, and either: 
   1. _For datasets not published in the EDI Data Repository_ - In the **Data Sources** textbox, enter a data source title and click **Add Data Source**. Fill out as much information about the source dataset as possible.
   2. _For datasets in the EDI Data Repository_ - In the **Data Sources** textbox click **Fetch Data Source Info from EDI**. Navigate to the dataset of interest and click on it. ezEML will automatically gather the metadata for the specified dataset.
2. Click **Save and Continue**

<div class="p-2">
  <div class="w-50 ratio ratio-16x9">
      <iframe src="https://youtube.com/embed/LkCA_qgDwhc" title="YouTube video" allowfullscreen=""></iframe>
  </div>
</div>

### EMLassemblyline

To create provenance metadata using [EMLassemblyline](https://ediorg.github.io/EMLassemblyline/):

1. Run the [`template_provenance()`](https://ediorg.github.io/EMLassemblyline/reference/template_provenance.html) function to create an empty provenance template.
2. For data sources originating from the EDI Data Repository, populate the template **dataPackageID** field with the EDI [data package identifier](/templates/resources/the-data-package.md#data-package-identifier) and specify "EDI" in the **systemID** field. Use the other fields of this template when creating provenance for data sources external to EDI Repository.
3. Run the [`make_eml()`](https://ediorg.github.io/EMLassemblyline/reference/make_eml.html) function to add the provenance metadata to the EML for the derived data.

### EDI Data Portal

To create provenance metadata from the [EDI Data Portal](https://portal.edirepository.org/nis/home.jsp) for the original dataset already residing in the EDI Repository:

1. Navigate to the **Provenance** section at the bottom of a data package [landing page](/templates/resources/data-package-pages.md). This section displays provenance information and includes a link to generate provenance metadata for the data package.

    <img class="screen-shot" src="/static/images/provenance-portal2.png" width="95%">

2. This links to the **Provenance Generator**. The **Provenance Metadata XML** tab contains text for the &lt;methodStep> element. Copy the entire &lt;methodStep> element.

    <img class="screen-shot" src="/static/images/provenance-generator.png" width="95%">

3. Open the EML for the derived data package in an XML editor and navigate to the &lt;methods> element. 
4. Paste the copied provenance &lt;methodStep> element at the end of the list of &lt;methodSteps>. Repeat for all data sources.

See [Editing EML](/templates/resources/creating-metadata-for-publication.md#editing-eml) for more on XML editors.

### EDIutils

To create provenance metadata from the [EDIutils](https://docs.ropensci.org/EDIutils/index.html) R Package:

1. Run the [`get_provenance_metadata()`](https://docs.ropensci.org/EDIutils/reference/get_provenance_metadata.html) function with the corresponding source [data package identifier](/templates/resources/the-data-package.md#data-package-identifier).
2. Add the returned &lt;methodStep> element into an EML R object of a derived data package or write it to file for other use cases.

For a language-agnostic solution, see the REST API documentation for [Get Provenance Metadata](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#get-provenance-metadata).

## Resources

* [End-to-End Provenance](https://github.com/End-to-end-provenance/End-to-end-provenance.github.io/blob/master/README.md) - Software tools to collect and use provenance information.
