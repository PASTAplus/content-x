# Create a Local Data Catalog for a Website

Local data catalogs allow researchers, projects, and organizations to present their data within the unique look and feel of their own website while providing access to the full metadata and other "data reuse" services offered in the EDI Data Portal.

EDI provides two prebuilt catalogs which can be easily embedded in an existing website. These catalogs are a searchable list of all the data packages belonging to a group and links back to the newest version of the data package in the EDI Data Portal. More advanced and customized catalogs can be implemented using the REST API.

<img src="/static/images/data-catalogs.png" width="100%">

[TOC]

## ezCatalog

This catalog is hosted on GitHub Pages and is easily embedded within a website. The data packages in this catalog are populated from a unique search query matching all the metadata from the EDI Data Repository that is pertinent while filtering out everything else that isn't.

Websites using this approach:

* [Niwot Ridge LTER](https://nwt.lternet.edu/data-catalog)
* [Jornada Basin LTER](https://lter.jornada.nmsu.edu/data-catalog/)
* [Beaufort Lagoon LTER](https://ble.lternet.edu/catalog)

To build this catalog, follow instructions in the [ezCatalog GitHub](https://github.com/clnsmth/ezCatalog) and [contact EDI](../support/contact-us.md) for assistance.

## Catalogs for OBFS members

[The OBFS Data Catalogs service](https://vocab.lternet.edu/ezcatalog/OBFS/) provides members of the Organization of Biological Field Station a way to create a searchable data catalog within minutes. The catalog includes data packages published to the EDI Data Repository and falling within a 10 km radius of the field station. The returned list of data packages can be modified by [contacting EDI](/templates/support/contact-us.md).

To build this catalog:

1. Go to [OBFS Data Catalogs](https://vocab.lternet.edu/ezcatalog/OBFS/)
2. Select a field station and click the **Submit** button to generate the catalog
3. Click the **embed** link at the top of the page to access options for adding the catalog to a web page
4. Select and copy an option
5. Paste the option into the body of a web page

Example:

```
<!DOCTYPE html>
<html>
<head>
<title>Data Catalog</title>
</head>
<body>

<h1>Adirondack Ecological Center - Data</h1>
<object type="text/html" width="100%" height="100%"
data="https://vocab.lternet.edu/ezcatalog/datacat.php?searchString=*&scope=*
&constraint=%28coordinates%253A%2522IsWithin%28ENVELOPE%28-75%2C-73%2C45%2C43%29%29%2522%29%2B
OR%2B%28*%3A*%2BAND%2Btitle%3A(ADIRONDACK)%29%2BOR%2B%28*%3A*%2BAND%2Bkeyword%3A(ADIRONDACK)%29
&form=htmltablejssearch">
</object>

</body>
</html>
```

## Advanced implementations

A possible motivation for an advanced catalog may be to provide a highly customized search interface or some feature or behavior not found in the EDI Data Portal. To do this, a query will need to be constructed to match all the metadata from the EDI Repository that is pertinent while filtering out everything else that isn't. This information is returned in XML and needs to be parsed and returned to the user.

[See this video](https://youtu.be/LwCI9TKi-Pg?t=361) for more on constructing a query and implementing advanced data catalog features.

## Resources

* **Build a Static Website** - Static websites are secure, low maintenance, free to host, fast, and easy to work with. [See this video](https://youtu.be/i4QczI3evGA) and [associated GitHub repository](https://github.com/BLE-LTER/LTER-website) to create a static website with a built-in data catalog.