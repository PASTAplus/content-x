# Use Cases for ezEML and EMLassemblyline

[ezEML](templates/resources/creating-metadata-for-publication#ezeml) and [EMLassemblyline](templates/resources/creating-metadata-for-publication#emlassemblyline) are EDI's tools for creating EML metadata. While both work well for the one-off data publication use case, they also support multiple use cases for an Information Manager that maintains data packages from one or more sites.

[TOC]

## ezEML

ezEML is a form-based online application designed to streamline the creation of EML-formatted metadata. When searching for an option to manage EML metadata, some information managers may be quick to dismiss ezEML as a viable option in favor of a scripted workflow. While the web interface may be limiting in some regards, ezEML's multitude of options for collaboration paired with its connectedness with the EDI repository make it an excellent option for handling data management tasks from creating, publishing, updating, and sharing EML.

### Transferring ezEML Data Packages

ezEML allows users to collaborate on EML creation through the [import and export](https://ezeml.edirepository.org/static/user_guide/importing.pdf?version=2022.04.25) of an ezEML Data Package. Further, users can directly [send ezEML data packages a colleague](https://ezeml.edirepository.org/static/user_guide/send_to_colleague.pdf?version=2022.04.25). These methods of transferring ezEML Data Packages between users serve an Information Manager well when they are:
 * Looking for Data Author input on a new EML document they are creating
 * Recieving ezEML Data Packages from Data Authors in order to review or publish to EDI

Methods for transferring ezEML Data Packages are highlighted in [this video](https://youtu.be/ouacOxpL0V4)

### Importing ezEML from EML

ezEML Data Packages can be created from EML metadata regardless of whether or not it was originally created with ezEML. These options for importing ezEML from EML should be of interest to any Information Managers who want to edit existing EML using ezEML, or that want to manage their corpus of data packages from ezEML.

#### Import EML File

ezEML Data Packages can be [imported from an EML/XML file](https://ezeml.edirepository.org/static/user_guide/importing_xml.pdf?version=2022.04.25). This is the best option if you have an EML document that has not yet been published to EDI that you would like to edit or manage with ezEML. 

#### Fetch a Package from EDI

Data packages that are [published on EDI can be fetched by ezEML](https://ezeml.edirepository.org/static/user_guide/fetch.pdf?version=2022.04.25). This is useful if you would like update an existing data package, create a new data package similar in structure to one that exists, or for managing your data packages within ezEML. Only the most recent revision of an EDI data package can be imported this way. Older revisions should be downloaded and imported manually (see above).

### Templates

ezEML templates allow information managers to host site- or project-specific, partially-filled ezEML data packages that can be accessed by anyone on ezEML. 

#### Creating Templates

Templates are created just like a normal ezEML data package. Once you've designed the template by filling in all of the fields that you expect one of your site's data authors would use, you can submit the template to EDI via teh **Send to EDI** button, or by exporting the template and emailing it directly support@environmentaldatainitiative.org. Remember to include a note stating that you would like to make the template available on ezEML.

> If you are not an LTER IM, or if you have not previously created templates for ezEML before, please first reach out to support@environmentaldatainitiative.org to confirm that we will be able to host a template for your group.

##### Design considerations for ezEML templates

When designing an ezEML template (or a series of ezEML templates), consider who will likely be using your template and which facets of EML will remain constant among that user base. Some examples of ezEML template designs:
 * A single template for a project that every dataset associated with the project should use could pre-fill information regarding funding information, point-of-contact, principal investigator, intellectual rights, and keywords. Whenever a scientist needs to publish their data from this project, the information manager can refer them to the same template.
 * Multiple templates for a field station could be broken down based on the geographic location of the sites. For example, the Piedraroja Field Station could have one template for each of the three stream sensor sites that produce data. While all templates share project-wide information, they each have a different geographic coverage. The template that a data collector from this field station would use depends on the location of their study.

An important thing to remember about ezEML templates is that their simplicity is their power. Since an ezEML template is really just a partially-filled ezEML data package, you have the freedom to design a suite of templates to best suit your organization's needs. A template that only pre-fills one or two fields goes along way to ensure that data is standardized across your organization. Finally, remember that a data author can augment, delete, or overwrite fields in a template if necessary. Consider developing lightweight documentation or how-to guides to inform your organization's data authors on the best way to utilize your templates.

#### Using Templates

[This resource](https://ezeml.edirepository.org/static/user_guide/templates.pdf?version=2022.04.25) explains how ezEML templates generally function within ezEML.

As mentioned above, after designing and creating ezEML templates, it is a good idea to document their intended use for your organization's data authors.

## EMLassemblyline

EMLassemblyline is an R package for creating high quality EML metadata and is optimized for automating recurring publications. For information managers comfortable working in R, EMLassemblyline offers a framework that combines scripted workflow with templates. EMLassemblyline tends to offer more options for creating specific elements in EML, such as dataset provenance and spatial elements. Its ability to run in automated workflows makes it an attractive option for maintaining ongoing datasets.

### Dataset Provenance

Source datasets used in the creation of a derived dataset can be described using the [`template_provenance()`](https://ediorg.github.io/EMLassemblyline/reference/template_provenance.html) function. Source datasets that are published on EDI can be referenced by their [data package identifier](templates/resources/the-data-package#data-package-identifier), while other data sources should referenced by their DOI.

### Spatial Elements

Functionality is being developed to support creation of EML's `<spatialVector>` and `<spatialRaster>` elements for geoJSON, KML, TIFF, and ESRI Shapefiles.

Stay tuned!

### Automated Data Publication

Recurring data publication was traditionally a manual edit and upload process that can now be automated with programmatic approaches (e.g. EAL) and use of data repository APIs (e.g. EDIutils). These approaches not only reduce effort, but improve metadata accuracy and enable automated workflows. Automated publication and upload is suitable for:
 * Ongoing data collection Data package is updated periodically with new data
 * Ongoing derived data product Data package is derived from sources with ongoing collection

Each use case is demonstrated [here](https://ediorg.github.io/EMLassemblyline/articles/auto_pub.html)


