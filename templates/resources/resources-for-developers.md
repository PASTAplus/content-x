# Resources for Developers  

The **EDI data repository** provides a range of services for developers who create applications and workflows that interact programmatically with our systems. Some common use cases:  

- **Programmatic Data Access** – Read and parse data into a preferred work environment to process and present to stake-holders.
- **Automated Workflows** – Build scripts or applications that upload or download data from the repository based on schedules or event notifications.  
- **Visual Data Exploration** – Provide an interactive interface for exploring data packages in the EDI repository.  

These are just a few examples—our services enable countless programmatic interactions with the EDI data repository.  

[TOC]

## REST API  

The [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html) allows developers to interact with the EDI repository programmatically. The API documentation provides details on available services, endpoints, and request formats.  

For R users, the [EDIutils](https://docs.ropensci.org/EDIutils/) R package offers an interface to the REST API, simplifying interactions with the repository.

For more information, see the [REST API page](/templates/resources/rest-api.md).


## EMLvp

[EMLvp](https://github.com/PASTAplus/EMLvp) is a Python 3 library designed to **validate and parse EML XML documents**, ensuring compliance with the EML metadata standard. It performs XML schema validation and checks that references resolve to existing IDs.  


## EMLassemblyline  

The [EMLassemblyline](https://ediorg.github.io/EMLassemblyline/) R package provides tools for programmatically creating and packaging Ecological Metadata Language (EML) metadata. This is particularly useful for automating the creation of metadata-rich data packages for upload to the EDI repository.
