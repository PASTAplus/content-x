# Adding a resource's physical information

Physical information such as file size, MD5 checksum, and number of rows in a table, are important pieces of metadata. When a resource is uploaded to ezEML or processed by EMLassemblyline, this information is automatically calculated. However, neither application can obtain this information from a file that is hosted externally. The responsibility is instead placed on the data provider to determine and manually enter this information.

## Calculating physical information

Physical information can usually be obtained for a file in a variety of ways. These methods may differ depending on the operating system of the computer.

### File size

On both Windows and Mac computers, file size can be found by right-clicking on the resource and selecting "WINDOWS_PLACEHOLDER" or "Get Info". Make sure to record the file size displayed in bytes.

<img src="/static/images/filesize-mac.png" width="15%">

### MD5 Checksum

To calculate the MD5 checksum of a file, you will want to use the Command Line (or Terminal) app on your Windows or Mac. From the command line, change your directory to where the file is located using the `cd` command. If you are on Windows, run the command `certutil -hashfile <file> MD5` where `<file>` is the filename:

<!-- <img src="/static/images/md5-win.png" width="15%"> -->

From a Mac, once you have changed your directory with `cd`, run the command `md5 <file>` (alternatively, type `md5` then drag and drop the file to Terminal): 

<img src="/static/images/md5-mac.png" width="15%">

### Number of rows

Calculating number of rows from a CSV file can be a little more tricky, especially if the file is too large to open in Excel or similar spreadsheet software.

If downloading the table from a database, obtain this information from the database using `SQL COUNT()`

From a Mac command line, the prompt `wc -l <file>` will count the number of line breaks in the file. This is perfectly useful information as long as you are certain that there are no line breaks within individual lines (such as in comment columns).

<img src="/static/images/numrows-mac.png" width="15%">

This command can be run from an R environment (Windows or Mac) with `system("wc -l <file>", intern = TRUE)`

<img src="/static/images/numrows-r.png" width="15%">


## Adding physical information to EML files

Physical information for a file can be inserted into an EML document to facilitate upload to the EDI repository.

### ezEML

To insert physical information for a table via [ezEML](https://ezeml.edirepository.org/eml/):

1. Navigate to the **Data Tables** tab and click the **Edit** button next to the data table.

<img class="screen-shot" src="/static/images/link-ezeml1.png" width="95%">

2. Enter the physical information for the table into the **Online Distribution URL** textbox. Remember to click **Save and Continue** before moving on.

<img class="screen-shot" src="/static/images/phys-ezeml.png" width="80%">

>This method can be replicated in the **Other Entities** tab as well. 

### EMLassemblyline

Physical information for a data table or other entity can be added using the `template_physical()` function (Coming Soon)

### Manually editing XML

If you've created a valid EML document using an ezEML creation tool, these attributes will already be created. To alter physical information for data tables or other entities manually:

1. Open the XML file in a text editor.
2. Within the &lt;dataTable> (or &lt;otherEntity>, &lt;spatialRaster>, or &lt;spatialVector>) element, the &lt;physical> element will contain a &lt;size> and an &lt;authentication> element, which should contain the attributes `unit = "bytes"` and `"method=MD5"`, respectively. Change the values of the &lt;size> and &lt;authentication> element, if necessary.
3. For the &lt;dataTable> element, the &lt;numberOfRecords> can be changed to reflect the number of rows in a table.

