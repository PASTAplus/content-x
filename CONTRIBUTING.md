<!-- Output copied to clipboard! -->

<!-- Yay, no errors, warnings, or alerts! -->


# CONTRIBUTING


## git structure

The active branch is `development`. `development` is merged into `main` for releases. Please submit your pull requests to `development`.


## Repository structure

The repository structure mirrors [web-x](https://github.com/PASTAplus/web-x) thereby enabling developers to build, link, and preview static web pages as they will be displayed in web-x.


## Design and goals

Content is organized into stand alone pages cross referencing each other. This modular design minimizes content duplication and maintenance. Focus on topics relevant to EDI users and not covered by other online resources (e.g. DataONE, NCEAS). Do summarize and reference other resources when relevant.


## General guidelines



* New pages - Before adding a new page, open an issue describing the content to be developed. Maintainers (the website team) will provide feedback and suggestions for cross referencing.
* File names - Replace spaces with dashes (e.g. new-page.md, new-image.png).
* Audience - Pages should target one of the three user classes: data author, data user, or information manager.
* Modularity - Each page should cover one topic with the goal of organizing information as modular building blocks.
* Introductory paragraphs - Each page should begin with an introduction/overview describing why the contents of the page are important and a brief overview of the concept or process the page covers. Pages should begin with little to no prerequisite knowledge. Build prerequisite knowledge in the opening paragraphs with reference to necessary information.
* Subsections - Use subsections to facilitate page navigation and content links.
* Be concise and minimize jargon.


## Formatting and style



* Markdown - Pages should be written using the [basic markdown syntax](https://www.markdownguide.org/basic-syntax/).
  * Note: Lists (enumerated and bulleted) must be both preceded and followed by an empty line to be rendered correctly in web-x.
* Voice - Pages should be written primarily in the first and third voice. The use of the second voice is acceptable when speaking directly to the audience (e.g. "Please contact us if you encounter an error") or in "imperative" contexts (e.g. providing step-by-step instructions).
* Section headers - Use the gerund form a verb for the header titles (e.g. "Using Download Links", "Uploading to EDI"). Don't use a gerund in headers or subheaders if it's redundant to the higher level (Title: Publishing a data package, Header: EDI Data Portal (good), Publishing via the EDI Data Portal (bad, redundant)). A counter example would be Header: Using Box Cloud Storage, Subheader: Creating a Box File Request (good, gerund is not redundant).
* References and links - References and links to online resources should be added as either:
    * Hyperlinked text to the target URL
    * The wikipedia reference format (i.e. The item being referenced is super scripted in square brackets<sup>[1]</sup> and the citation is listed in a "References" section at the bottom of the page).


## Images


### Creating images



1. Create an image with high enough resolution so that it isn't distorted at its intended magnification and when enlarged to approximately twice its intended size. Generally, screenshots from a web browser should be taken at normal 100% magnification.
2. Trim white space from around the image.
3. Compress the image to reduce file size. Use the [tinypng.com](https://tinypng.com/) web service to do this.


### Adding images to markdown

1. Add the image file to the `/static/images` directory. 
2. Reference the image from within a markdown page using HTML. There are 4 use cases:
   1. Screenshots - A drop shadow is added to screenshots to help distinguish them from the body text. This is done with the `screen-shot` CSS class. Example:
   
   `<img class="screen-shot" src="/static/images/ezeml-send-revision.png" alt="Send ezEML revision" width="85%">`

   2. Figures with captions - Example:
   
   ```
   <div class="figure_featured" style="width: 25%;">
     <figure>
       <img src="/static/images/featured_data/aquatic-microcosm.png" alt="aquatic microcosm"/>
       <figcaption class="figure-caption">Fig. 1: Principal components of a Standardized Aquatic Microcosm ...</figcaption>
     </figure>
   </div>
   ```
   
   > NOTE: Featured data images to use on the website home page as well as in the grid page cards is specified by adding an `id="pickme"` parameter to the `<img>` tag of a featured dataset image. If none is specified, the first image of the featured data will be used. Example:
   > ```
   > <div class="figure_featured" style="width: 25%;">
   >   <figure>
   >     <img id="pickme" src="/static/images/featured_data/aquatic-microcosm.png" alt="aquatic microcosm"/>
   >     <figcaption class="figure-caption">Fig. 1: Principal components of a Standardized Aquatic Microcosm ...</figcaption>
   >   </figure>
   > </div>
   > ```

   3. All other image types - Example:

   `<img src="/static/images/metadata-in-the-research-life-cycle.png" alt="Creating metadata in the research life cycle" width="55%">`


3. Resize for display in the GitHub preview. The general rule of thumb is that the image should be sized so normal body text displayed in the images should match text size on the web page. Set the image size using the `width` parameter and use a unit of `%`, meaning percent width of the page view port.

> NOTE: A blank newline is required before and after the HTML snippet for markdown to render correctly in HTML.

## Videos

### Embedding videos

Whether embedding videos within a news article or resource page, use HTML and Bootstrap following the example below:

```
<div class="p-2">
  <div class="w-50 ratio ratio-16x9">
      <iframe src="https://youtube.com/embed/Dq8ew4Iad60" title="YouTube video" allowfullscreen=""></iframe>
  </div>
</div>
```

> NOTE the `/embed/` component of the YouTube video link above. You must manually insert this into a YouTube URL when creating the HTML block.

## Terminology

Consistent terminology conveys coherence and makes editing across all web pages, through search and replace methods, much simpler. Below is the current implementation of terminology throughout web pages:



* Capitalize EDI services and features - These are proper nouns (e.g. "EDI Data Portal")
* "EDI Data Repository" or "EDI Repository" not "EDI Data Commons"
* Use "research" instead of "science". Research is more diverse, science is more specific.
* Use "data/dataset" and "metadata" before publication & "data package" after publication.
* Use "publish" over "archive" to build off the "article publishing" schema.
* Prioritize "data publication" over "published data package"
* Prefer "EDI Data Repository" to "PASTA" whenever possible.
* Use "REST API" not "API".
* Use "Information Manager (IM)" not "Data Manager (DM)"
* Use "search data" not "find data" and "discover"data
* "EDI Data Curation Team" or "EDI Curation Team" or "EDI curators"
* Prefer "data file" over "data object" and "data entity" -  The latter two are non-colloquial
* Use "EML file" when referencing the file object and "EML" or "EML metadata"  when referring to content in the file.
* Possessive apostrophes -  don't use possessive apostrophes to denote ownership of non-living entities (e.g. "the EDI Repository's" or "a data packages'")
* Use official terminology to establish consistency when referencing an EDI feature (e.g. "EDI Data Portal") rather than variations thereof (e.g. EDI repository interface).
* Use "Data package landing page" or "Data package summary page" and "Full metadata page".


## Format

* Code - Use code highlighting when referencing code, functions, and parameters.
* Functions - Format using `function_name()`
* Colon before a list
* Use bold when referencing terms/items on page,  not quotes or code highlighting.
* EML elements are listed verbatim as they appear in the schema (i.e. camel case and within "&lt;" and ">" tags). Only do this in the context of EML metadata, which is typically technical documentation targeting the information manager and advanced user.
* Use enumerated lists when describing a sequential process.
* Be precise when linking to content in other pages - Link directly to a topic sub-section rather than just the parent page.
* Quotes - Replace smart quotes and apostrophes with dumb quotes and apostrophes
* Spaces - Replace all double spaces with single spaces. Single spaces after periods.

## Create a News article

To create a news article:
1. Copy the template below and paste into a new file in the `/templates/news` directory.
2. The file name should follow `news-YYYYMMDD.XX.md`, where `YYYYMMDD` is the date the article was created, `XX` is the news article created on that date (use `00` if only one article was published on that day).
3. Update the TITLE, DATE, AUTHOR, and CONTENT placeholders.
4. Commit changes and push to the content-x GitHub.
5. Notify the website team that new content has been added and they will integrate your work into the website.

```
# News

## ADD TITLE HERE

ADD DATE HERE (e.g. April 20, 2022)

ADD ARTICLE AUTHOR HERE

### Description

ADD CONTENT HERE

<!-- News -->
```

## Create a Featured Data article

To create a new featured data article:
1. Copy the template below and paste into a new file in the `/templates/featured` directory.
2. The file name should follow `featured-YYYYMMDD.XX.md`, where `YYYYMMDD` is the date the article was created, `XX` is the news article created on that date (use `00` if only one article was published on that day).
3. Update the TITLE, DATE, AUTHOR, and CONTENT placeholders.
4. Images should be added to the `/static/images/featured_data` directory and referenced from there.
5. Commit changes and push to the content-x GitHub.
6. Notify the website team that new content has been added and they will integrate your work into the website.

```
# Featured Data

## ADD TITLE HERE

ADD DATE HERE (e.g. March 1, 2021)

ADD ARTICLE AUTHOR HERE

### Citation

ADD CITATION HERE

### Description

ADD CONTENT HERE

<!-- Images used in articles follow the HTML format below. Adjust the "width" parameter to resize. 
Identify the primary image to use with the featured data display on web-x home page and on the featured 
data grid page by adding an id="pickme" parameter to the HTML, if not specified, the first image of the 
page will be used.-->

<div class="figure_featured" style="width: 25%;">
    <figure>
       <img id="pickme" src="/static/images/featured_data/MYIMAGE.png" alt="ADD DESCRIPTION OF IMAGE"/>
       <figcaption class="figure-caption">ADD CAPTION HERE</figcaption>
    </figure>
</div>

#### Data sources for the database include

### References

### [All featured data contributions](/templates/featured/featured-grid)

```
