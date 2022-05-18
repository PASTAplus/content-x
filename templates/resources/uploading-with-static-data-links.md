# Uploading with Static Data Links

A static URL resolving to a data file can be inserted into the physical/distribution element of an EML file and serve as a data source when uploading to the EDI Data Repository. This can be useful for bypassing the 500 MB size limit of manual uploads on the EDI Data Portal, for facilitating workflow automation, and for handling files that may be too large to transfer directly to a data curator.

Any static download URLs that do not offer redirects can serve as the data source in an EML document. A locally managed web server or cloud hosting service are both viable options for generating these links. [Box Cloud Storage](https://www.box.com/) is an example cloud service that allows for generating links that do not offer any redirects and are static.

<img src="/static/images/download-links.png" width="15%">

> Is your data link static? Use the [Redirect Detective](https://redirectdetective.com/index.html) service to find out.

[TOC]

## Using Box Cloud Storage

Files stored on a Box Cloud Storage application can be directly downloaded via a static URL. 

>A paid/premium Box account is required for generating direct download links or receiving files through a file request.


### Creating a Box File Request

A File Request link allows anyone (with or without a Box account) to submit files to a directory in a Box account. They offer a good solution for collecting prohibitively large data from submitters that require static links. To create a request:

1. Navigate to the directory (from within the Box web application while logged into a premium account) where data files should be submitted.
2. Click the **File Request** button on the right side of the screen which will open a pop-up.

<img class="screen-shot" src="/static/images/file-request1.png" width="100%">

3. On the pop-up screen, set the link to enabled. This selection should be reflected on the first **File Request** button pressed.

<img class="screen-shot" src="/static/images/file-request2.png" width="100%">

4. Copy the shareable link from the pop-up screen and try it in a web browser. This link should lead to a page that looks like the one below.

<img class="screen-shot" src="/static/images/file-request3.png" width="85%">

5. Share this link with a data submitter. They will not need to have a Box account to submit data to this directory.

### Creating a static download link

A static download link will function as a data source for the EDI Data Repository. To create a static download link:

1. Navigate to the directory that contains the data file for which to create a link. Click on the link icon which will open a pop-up window.

<img class="screen-shot" src="/static/images/static-link1.png" width="100%">

2. DO NOT use the Share Link from this window for direct download. Instead, click on the **Link Settings** button which will open another pop-up window.

<img class="screen-shot" src="/static/images/static-link2.png" width="55%">

3. In the shared link settings, at the bottom of the page, find and copy the direct link URL. 

<img class="screen-shot" src="/static/images/static-link3.png" width="55%">

## Adding download links to EML files

Direct download links of any type, and static links generated from a Box account, can be inserted into an EML document to facilitate upload to the EDI Data Repository.

### ezEML

To insert a download link via [ezEML](https://ezeml.edirepository.org/eml/):

1. Navigate to the **Data Tables** tab and click the **Edit** button next to the data table.

<img class="screen-shot" src="/static/images/link-ezeml1.png" width="95%">

2. Paste the link into the **Online Distribution URL** textbox. Remember to click **Save and Continue** before moving on.

<img class="screen-shot" src="/static/images/link-ezeml2.png" width="80%">

The data table will now be associated with the provided download link. Submit to EDI via **Send to EDI** or download the XML document with the **Download EML File** button.

>This method can be replicated in the **Other Entities** tab as well. 
>If you are not uploading data resources to ezEML, and want to maintain a fully offline workflow, remember to manually [add physical metadata information](/templates/resources/adding-physical-information.md). 


### EMLassemblyline

To insert a download link via [EMLassembylline](https://ediorg.github.io/EMLassemblyline/index.html):

1. Supply the link as a character string to the `data.table.url` or `other.entity.url` arguments in the [`make_eml()`](https://ediorg.github.io/EMLassemblyline/reference/make_eml.html) function. To add multiple links, supply links as a vector of character strings.

<img class="screen-shot" src="/static/images/link-eal1.png" width="70%">

2. Run [`make_eml()`](https://ediorg.github.io/EMLassemblyline/reference/make_eml.html) to associate the tables with the provided links and return an EML file.

<img class="screen-shot" src="/static/images/link-eal2.png" width="70%">

>If you are using EMLassemblyline with web-hosted data resources, and want to maintain a fully offline workflow, remember to manually [add physical metadata information](/templates/resources/adding-physical-information.md). 

### Manually editing XML

To insert download links manually:

1. Open the XML file in a text editor. Within the &lt;dataTable> (or &lt;otherEntity>, &lt;spatialRaster>, or &lt;spatialVector>) element, add &lt;distribution>, &lt;online>, and &lt;url> elements to the &lt;physical> element.

2. Ensure that the elements are properly nested, and that the function attribute is set to "download". 

## Uploading to EDI

>If creating a data package with ezEML, the easiest way to upload to the EDI Repository is by using the **Send to EDI** tab.

>If you've manually added download links to an EML file or have created a data package with EMLassemblyline, and don't have an EDI User Account, you can submit the EML document by emailing the EDI Curation Team and requesting that they upload it on your behalf. Make sure that every data file in the data package has a direct download link associated with it. There is no need to attach the data files in the email since the download links are listed.

If publishing a data package via the EDI Data Portal note:



1. In order to skip manual upload, all objects must have links (all or nothing).
2. Remember to **NOT** check the "Manually upload data" checkbox.
3. If some of the objects in the data package package are already in the EDI Repository, remember to check the **Allow PASTA+ to skip …** checkbox.

<img class="screen-shot" src="/static/images/upload-link.png" width="70%">
