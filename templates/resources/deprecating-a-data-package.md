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

Execute a "soft delete" of the data package. Any data package owner can perform this operation using [cURL](https://en.wikipedia.org/wiki/CURL) or another HTTP-based application that can send a "DELETE" request. The delete method is described in the [API documentation](https://pasta.lternet.edu/package/docs/api#DELETE%20:%20/eml/%7Bscope%7D/%7Bidentifier%7D). Note that the entire series will be "soft deleted", so use only the data package scope and identifier in the DELETE request. To perform a "soft delete" using `cURL` you would need to set the "user" and "request method" parameters to identify the owner of the data package and the `DELETE` mehtod. The full `cURL` command would look like

```
curl --user <USER>:<PASSWORD> -X DELETE <URL>
```

The PASTA API requires the "user" parameter to be the full EDI LDAP distinguished name (e.g., `uid=ecoridge,o=EDI,dc=edirepository,dc=org`), where the "uid" field is the identifier used to login into the Data Portal when publishing a data package.

For example, the command

```
curl --user 'uid=ecoridge,o=EDI,dc=edirepository,dc=org:asd9wkjas38' -X DELETE 'https://pasta.lternet.edu/package/eml/edi/7'
```

will "soft delete" all data package revisions of the **edi.7** series in the EDI production environment. To perform a "soft delete" on your data package replace the identifier "ecoridge" and the password "asd9wkjas38" with your own user identifier and password. You may also perform a "soft delete" in the EDI staging environment by replacing `pasta.lternet.edu` with `pasta-s.lternet.edu` in the URL.

> Please [contact us](/templates/support/contact-us.md) if you need help deleting a data package.
