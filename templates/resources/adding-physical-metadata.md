# Adding Physical Metadata

Physical metadata such as file size, MD5 checksum, and number of rows in a table, are important pieces of information. This information is not only useful to future users who are assessing fitness of a data package for reuse, but also can be used to verify the integrity of files after uploads and downloads. When a resource is uploaded to ezEML or processed by EMLassemblyline, this information is automatically calculated. However, neither application can obtain this information from a file that is not accessible. The responsibility is instead placed on the data provider to determine and manually enter this physical metadata.

[TOC]

## Calculating physical metadata

Physical metadata can usually be obtained for a file in a variety of ways. These methods may differ depending on the operating system of the computer.

### File size

On both Windows and Mac computers, file size can be found by right-clicking on the resource and selecting "Properties" or "Get Info". Make sure to record the file size displayed in bytes.

<img class="screen-shot" src="/static/images/filesize-mac.png" width="60%">

### MD5 checksum

To calculate the MD5 checksum of a file, you will want to use the Command Line (or Terminal) app on your Windows or Mac. From the command line, change your directory to where the file is located using the `cd` command. If you are on Windows, run the command `certutil -hashfile <file> MD5` where `<file>` is the filename:

From a Mac, once you have changed your directory with `cd`, run the command `md5 <file>` (alternatively, type `md5` then drag and drop the file to Terminal): 

<img class="screen-shot" src="/static/images/md5-mac.png" width="50%">

This command can be run from an R environment (Windows or Mac) with `md5sum(<file>)`, where `<file>` is the full path to the entity.

### Number of rows

Calculating number of rows from a CSV file can be a little more tricky, especially if the file is too large to open in Excel or similar spreadsheet software.

If downloading the table from a database, obtain this information from the database using `SQL COUNT()`

From a Mac command line, the prompt `wc -l <file>` will count the number of line breaks in the file. This is perfectly useful information as long as you are certain that there are no line breaks within individual lines (such as in comment columns).

<img class="screen-shot" src="/static/images/numrows-mac.png" width="50%">

This command can be run from an R environment (Windows or Mac) with `system("wc -l <file>", intern = TRUE)`

<img class="screen-shot" src="/static/images/numrows-r.png" width="40%">

### Record delimiter

The record delimiter, or end of line character, marks the end of each line (or record) in a file. There are generally three flavors of record delimiter, a line feed (`\n`), a carriage return (`\r`), and a combination carriage return line feed (`\r\n`). When determining which record delimiter your file uses, consider which operating system was used to create your file. Mac OS files will use the line feed (`\n`), while files created on a Windows machine will use the combination carriage return line feed (`\r\n`). The single carriage return (`\r`) was used by older Macs and is typically not seen anymore.

If the origin of the file is uncertain, you can determine the record delimiter by using a text editing application like [Notepad++](https://notepad-plus-plus.org/). From Notepadd++:

1. Open the file.
2. Select the menu item `View > Show Symbol > Show End of Line`.
3. Go to the end of a line to see the record delimiter. It will display `CR LF` or `LF` whether the record delimiter is combination carriage return line feed or just line feed. In the very rare case that the record delimiter is just carriage return, it will display `CR`.

## Adding physical metadata to EML

Physical information for a file can be inserted into an EML document to facilitate upload to the EDI repository.

### ezEML

To insert physical information for a table via [ezEML](https://ezeml.edirepository.org/eml/):

1. Navigate to the **Data Tables** tab and click the **Edit** button next to the data table.

    <img class="screen-shot" src="/static/images/link-ezeml1.png" width="75%">

2. Enter the physical information for the table into the **Online Distribution URL** textbox. Remember to click **Save and Continue** before moving on.

    <img class="screen-shot" src="/static/images/phys-ezeml.png" width="60%">

>This method can be replicated in the **Other Entities** tab as well. 

### EMLassemblyline

Physical information for a data table or other entity can be added using the `template_physical()` function (Coming Soon)

### Manually editing XML

If you've created a valid EML document using an ezEML creation tool, these attributes will already be created. To alter physical information for data tables or other entities manually:

1. Open the XML file in a text editor.
2. Within the `<dataTable>` (or `<otherEntity>`, `<spatialRaster>`, or `<spatialVector>`) element, the `<physical>` element will contain a `<size>` and an `<authentication>` element, which should contain the attributes `unit = "bytes"` and `"method=MD5"`, respectively. Change the values of the `<size>` and `<authentication>` element, if necessary.
3. For the `<dataTable>` element, the `<numberOfRecords>` can be changed to reflect the number of rows in a table.

