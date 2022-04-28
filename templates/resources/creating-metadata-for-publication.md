# Creating Metadata for a Data Package

Metadata describe the structure and context of other data. They are vital to the discovery and reuse of data, and are a required element of a [data package](/templates/resources/the-data-package.md).

<img src="/static/images/describe.png" width="10%"> 

This document introduces the concept of metadata and the Ecological Metadata Language (EML) format, used by the EDI Data Repository. It also details the tools available for creating and editing EML, and provides a brief introduction to best practices for creating EML.

[TOC]

## What is metadata?

Generally, metadata for observational data focuses on:

* **WHAT** is the content of the data?
* **WHO** collected the data?
* **WHEN** were the data collected?
* **WHERE** were they collected?
* **HOW** were the data collected?

It is beneficial to begin compiling metadata at the start of [the research life cycle](/templates/resources/creating-metadata-during-the-research-lifecycle.md) and have a completed metadata for each dataset by the end of it. The information that is supposed to be retained in metadata is prone to quickly degrade if not recorded.

<figure class="figure">
   <img src="/static/images/information_loss.png" class="figure-img" width="65%"/>
   <figcaption class="figure-caption">Figure and caption from Michener et al. 1997<sup>[2]</sup>: Example of the normal degradation in information content associated with data and metadata over time ("information entropy"). Accidents or changes in technology (dashed line) may eliminate access to remaining raw data and metadata at any time.</figcaption>
</figure>

## The Ecological Metadata Language (EML)

The [Ecological Metadata Language (EML)](https://eml.ecoinformatics.org/) is an XML metadata standard: a metadata schema that is maintained by a group of interested parties and optimized for the ecological and environmental sciences. The EML specification defines the content ("elements"), characteristics ("attributes"), and relationships ("hierarchy") that composes an EML file.<sup>[1]</sup> 

Some key elements of an EML file are presented in relation to these categories of focus:

### WHAT is the content of the data?

In the EML document, the &lt;title>, &lt;abstract>, and &lt;keywords> elements are used to describe the content of a dataset. Further, &lt;attribute> and &lt;unit> elements are used in conjunction with &lt;dataTable>, &lt;spatialVector>, and &lt;otherEntity> elements to describe specific data objects in detail.

### WHO collected the data?

The &lt;creator> element describes the personnel who lent intellectual input towards the creation of the data package. The &lt;associatedParty> element can be used for personnel who made some contribution but will not receive attribution in a citation (i.e. field crew, lab technicians, temporary help).


### WHEN were the data collected?

The &lt;temporalCoverage> element stores the start and end date of the data.


### WHERE were the data collected?

The &lt;geographicCoverage> element is used to explicitly describe the location where the research occurred. This element allows for the verbal description of locations as well as bounding coordinates. 

### HOW were the data collected?

The &lt;methods> element should be used to describe how data were collected. The information on "how" or "provenance" may be supplemented with data processing scripts and documentation of other data used.

## EML best practices

For more on EML best practices see the [EDI Data Package Best Practices](https://ediorg.github.io/data-package-best-practices/).

## Creating EML

Since the EML standard was designed to handle an enormous variety of data scenarios, EML is complex and the learning curve to creating it can be steep. EDI develops and maintains a couple tools, ezEML and EMLassemblyline, to make this process easier and allow data providers to focus on the content of their metadata. Each tool serves a slightly different use case and data providers can transfer metadata between tools to meet their needs. Both the ezEML and EMLassemblyline tools allow users to work on metadata incrementally and return to a saved state at a later time.

See the resources section at the bottom of this page for more tools to create EML metadata.

### ezEML

[ezEML](https://ezeml.edirepository.org/) is a form-based online application designed to streamline the creation of EML-formatted metadata. Despite the complexity of EML, many data scenarios require only a relatively small subset of fields to be filled out. In such scenarios, ezEML can greatly simplify the process of creating EML, especially for users who are new to EML or use it only infrequently.

ezEML can be used as a "wizard" leading the user through EML document creation step by step, or it can be used in a more user-directed fashion. Among other things, ezEML supports:

* Collaboration on EML creation through the [import and export](https://ezeml.edirepository.org/static/user_guide/importing.pdf?version=2022.04.25) feature
* Data submission to an information manager for review through the [send to colleague](https://ezeml.edirepository.org/static/user_guide/send_to_colleague.pdf?version=2022.04.25) feature
* Importing an [existing EML file](https://ezeml.edirepository.org/static/user_guide/importing_xml.pdf?version=2022.04.26) or [EDI published data package](https://ezeml.edirepository.org/static/user_guide/fetch.pdf?version=2022.04.26) to work with it in ezEML
* Sharing boiler plate metadata common to a research group/site with colleagues via the [ezEML templates](https://ezeml.edirepository.org/static/user_guide/templates.pdf?version=2022.04.26) feature
* Checking the EML for correctness and completeness

There are a variety of options to help new users learn ezEML:

* [About](https://ezeml.edirepository.org/eml/about)
* [User Guide](https://ezeml.edirepository.org/eml/user_guide)
* [ezEML overview video](https://studio.youtube.com/video/LVRoFmTwvtU/edit)
* [ezEML YouTube playlist](https://www.youtube.com/playlist?list=PLi1PZkcSXdAKTtpgyHnd8GjtL6kRMMGFR)

### EMLassemblyline

[EMLassemblyline](https://ediorg.github.io/EMLassemblyline/) is an R package for automating the creation of EML metadata within [programmatic workflows](https://ediorg.github.io/EMLassemblyline/articles/auto_pub.html). EMLassemblyline supports the same set of metadata elements as ezEML and is extensible through the [EML R package](https://docs.ropensci.org/EML/). While it is optimized for automation, it also works well for creating a single EML metadata file.

Among other things, EMLassemblyline supports:

* Importing an [existing EML file](https://ediorg.github.io/EMLassemblyline/reference/eml2eal.html) to work with it in EMLassemblyline
* Checking the EML for correctness and completeness

Learn more about using EMLassemblyline on the [project website](https://ediorg.github.io/EMLassemblyline/).

## Editing EML

EML documents can be updated or edited using the software with which they were created (ezEML, EMLassemblyline). While this is likely the easiest way to make most edits to an EML file, it is sometimes necessary to manually edit EML in order to incorporate elements outside of the applications' scopes. Also, at times it's simpler because minor edits can be completed faster manually. While any text editor can be used to edit an EML file, XML-specific software have added capabilities to streamline the editing process and support schema validation.

### oXygen XML Editor

<a href="https://www.oxygenxml.com" title="Oxygen XML Editor"><img src="https://www.oxygenxml.com/img/resources/oxygen190x62.png" width="150" alt="Oxygen XML Editor" border="0"/></a>

The [oXygen XML Editor](https://www.oxygenxml.com/) is a commercial product that provides a comprehensive suite of XML authoring and development features:

* [Academic pricing, or free license](https://www.oxygenxml.com/non_profit_program.html)
* Schema validation
* Instant auto-complete
* Other view modes

### jEdit

[jEdit](http://www.jedit.org/) is an open source and free editor providing the basics most users would need:

* Good general text editor
* XML plug-in
* Schema validation
* Auto-complete

## Resources

Additional resources for creating and managing EML metadata:

* [EML](https://docs.ropensci.org/EML/) - An R package for constructing EML. EMLassemblyline is a wrapper to this package.
* [metapype-eml](https://github.com/PASTAplus/metapype-eml) - A Python package for constructing EML. ezEML is based off this.
* [LTER Core-Metabase](https://github.com/lter/LTER-core-metabase) - A PostgreSQL RDB model for research groups managing large volumes of EML metadata.

## References

<sup>[1]</sup>Matthew B. Jones, Margaret O'Brien, Bryce Mecum, Carl Boettiger, Mark Schildhauer, Mitchell Maier, Timothy Whiteaker, Stevan Earl, Steven Chong. 2019. Ecological Metadata Language version 2.2.0. KNB Data Repository. doi:10.5063/F11834T2

<sup>[2]</sup>Michener, W.K., Brunt, J.W., Helly, J.J., Kirchner, T.B. and Stafford, S.G. (1997), NONGEOSPATIAL METADATA FOR THE ECOLOGICAL SCIENCES. Ecological Applications, 7: 330-342. https://doi.org/10.1890/1051-0761(1997)007[0330:NMFTES]2.0.CO;2
