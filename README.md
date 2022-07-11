# content-x
Repository for static content of the EDI [website](https://edirepository.org/) ([web-x](https://github.com/PASTAplus/web-x#development-notes)).

## Web pages
Web pages (in markdown format) are organized into subdirectories of `templates/`. This directory structure mirrors that of web-x thereby enabling content-x developers to build, link, and preview pages in the same way they will be displayed on web-x. This essentially makes content-x a "development" environment of web-x.

Sub-directories of `templates/` loosely represent the main menu structure of web-x. Pages should be organized accordingly with all orphaned pages (i.e. those not linked to directly from the menu) stored in `resources/`.

## Images
`static/images/` contains images referenced in markdown pages. Use the [tinypng.com](https://tinypng.com/) service to compress images before adding here.

## Contribute

See the [contributing guidelines](/CONTRIBUTING.md).

Contribute by type:
* [Create a News article](https://github.com/PASTAplus/content-x/blob/main/CONTRIBUTING.md#create-a-news-article).
* [Create a Featured Data article](https://github.com/PASTAplus/content-x/blob/main/CONTRIBUTING.md#create-a-featured-data-article).
