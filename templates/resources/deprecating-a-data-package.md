# Deprecating a Data Package

Deprecation enables data authors to discourage the continued use of a data package, in favor of a better alternative. It's typically applied when data issues cannot be resolved through a [data package update](/templates/resources/updating-a-data-package.md), or when maintenance of a data package has moved to a new [data package series](/templates/resources/the-data-package.md#versioning-data-packages). 

Deprecation involves posting a prominent notification of the change and removal of the data package from the EDI search index. This "soft delete" hides the data package from new potential users but keeps it accessible to existing users that already have a direct link (e.g. DOI). In essence, this discourages use while preserving the persistence and immutability required by Open Data and Reproducible Research.

> Note, only under extreme circumstances do we completely remove a data package from existence. Such situations are handled carefully on a case-by-case basis.

[TOC]

## Step 1 - Notify users about the deprecation

Notify users about the deprecation by adding "DEPRECATED" in both the title and abstract of the data package metadata. Also, in the first paragraph of the abstract, describe the reasons for the change and any links to superseding data packages. Our [support of Markdown](/templates/news/news-20210430.00.md) in title and abstract text provides some liberty with sizing and formatting (e.g., bold).

> Tip: Use the [Metadata Previewer](https://portal.edirepository.org/nis/metadataPreviewer.jsp) to see how the changes will render in the EDI Portal before publishing.

An example data package deprecation notice:

<img class="screen-shot" src="/static/images/deprecation-notice.png" alt="Deprecation notice" width="85%">

Once the metadata edits are complete, the changes will have to be uploaded via [data package update](/templates/resources/updating-a-data-package.md).

## Step 2 - "Soft delete" the data package

Execute a "soft delete" of the data package. Any data package owner can perform this operation using [curl](https://en.wikipedia.org/wiki/CURL) or another HTTP-based application that can send a "DELETE" request. The delete method is described in the [API documentation](https://nam02.safelinks.protection.outlook.com/?url=https%3A%2F%2Fpasta.lternet.edu%2Fpackage%2Fdocs%2Fapi%23DELETE%2520%3A%2520%2Feml%2F%257Bscope%257D%2F%257Bidentifier%257D&data=05%7C01%7Cjfutrelle%40whoi.edu%7C4786c822c02c43dedc0d08dabce50e7e%7Cd44c5cc6d18c46cc8abd4fdf5b6e5944%7C0%7C0%7C638029989235147987%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C3000%7C%7C%7C&sdata=ewGg%2BUuazIME6VLxGHE2hjVBXr51p8uVdXxRmSZeEE8%3D&reserved=0). Note that the entire series will be "soft deleted", so use only the data package scope and identifier in the DELETE request. For example the command

```
curl --user 'uid=NES,o=EDI,dc=edirepository,dc=org:<PASSWORD>' -X DELETE 'https://pasta.lternet.edu/package/eml/knb-lter-nes/7'
```

will "soft delete" all data package revisions in the **knb-lter-nes.7** series.

> Please [contact us](/templates/support/contact-us.md) if you need help deleting a data package.
