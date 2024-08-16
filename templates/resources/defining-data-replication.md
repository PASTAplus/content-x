# Defining Data Package Replication

Ensuring data consumers are aware of replicated data across repositories is crucial for reducing data user confusion, data misuse and errors, and inefficiencies for data harvesters.

The [Ecological Metadata Language](https://eml.ecoinformatics.org/eml-ecological-metadata-language) (EML v2.2.0) offers a semantic annotation feature suitable for defining data replication, applicable to both entire data packages and specific data entities within a package. This functionality in combination with the [schema:sameAs](https://schema.org/sameAs) property enables a solution for indicating replicated data resources that align with [Science-On-Schema.Org](https://github.com/ESIPFed/science-on-schema.org/blob/master/guides/Dataset.md) conventions, promoting dataset discovery and interoperability.

EML provides two locations to express `schema:sameAs` relationships through annotations, within a [DatasetType](https://eml.ecoinformatics.org/schema/eml-dataset_xsd#DatasetType), and an [EntityGroup](https://eml.ecoinformatics.org/schema/eml-entity_xsd.html#EntityGroup).

[TOC]

### DatasetType

This location indicates relationships between data packages. Semantic RDF structures the data package as the subject, related to another package as the object. The annotation element is inserted at the XPath: `/eml/dataset/annotation`. For example:

```xml
<annotation>
      <propertyURI label="sameAs">https://schema.org/sameAs</propertyURI>
      <valueURI label="Data used to …">https://doi.org/10.5066/F7VX0DMQ</valueURI>
</annotation>
```

Where the `valueURI` label is the dataset title and the value is the dataset Digital Object Identifier (DOI). This annotation reads: "This dataset is the same as the dataset identified by [https://doi.org/10.5066/F7VX0DMQ](https://doi.org/10.5066/F7VX0DMQ)".


### EntityGroup

This location is used to indicate relationships between data entities (e.g. dataTable or otherEntity). RDF expresses the data entity as the subject, related to another entity as the object. The annotation element is inserted within the EntityGroup. For example:

```xml
<annotation>
      <propertyURI label="sameAs">https://schema.org/sameAs</propertyURI>
      <valueURI label="black_sand_phe …">https://pasta.lternet.edu/package/data/eml/…</valueURI>
</annotation>
```

Where the `valueURI` label is the data entity name. This annotation reads: "This data entity is the same as the entity defined by [https://pasta.lternet.edu/package/data/eml/knb-lter-nwt/237/1/39dbac0784a042fcda990797377e27ee](https://pasta.lternet.edu/package/data/eml/knb-lter-nwt/237/1/39dbac0784a042fcda990797377e27ee), which is a download link to a data entity in the EDI repository.

_One issue to be aware of here is that persistent identifiers (e.g. DOI) are typically not minted for data entities. Therefore, the resolvability of the object, depends on the stability of the link used in the annotation._

### Mutable Series Consideration

A potential challenge arises when the valueURI is a data package DOI, and pointing to the latest version within a mutable data package series. This can lead to conflicting interpretations of the relationship between data packages. For instance, if `schema:sameAs` expresses a relationship between two data packages, but a significantly different version of the object (data package in the other repository) is published, the relationship becomes inaccurate. Notably, [DataONE](https://www.dataone.org/) employs this practice for harvested data packages presented to users.

A solution to this issue is to never use a URI in an annotation that points to a mutable object, even if it means ignoring a DOI in favor of another style of PID. This way, the object being referenced would always be traceable through the PID (not the DOI) even if the DOI is transferred to reference the latest version of the object.