# Changing Permissions on a Data Package

The permissions governing who can make changes to a data package are set in access control rules of the EML metadata file of the most recent data package version. To change the permissions, the current EML file must be edited as a revision to the data package and uploaded by one of the users in current list of access control rules.

> Only EDI user accounts are allowed to upload directly to the repository. Google, GitHub, and ORCID accounts are not EDI user accounts. If you are not an EDI user, you will need to work with someone who is to upload the updated EML file.
> 
> [Contact us](https://edirepository.org/support/contact-us) for assistance.

[TOC]

## Checking permissions

To check permissions on a current date a package:

1. Go to the [full metadata page](/templates/resources/data-package-pages) of the data package.
2. Click the **View EML as XML** button at the lower left-hand corner of the page.
3. Search for the `<access>` element in the EML XML. 
4. Each `<allow>` element nested within `<access>` represents a user ID and the associated permissions. In the example below, the users `EDI` and `sbashevkin` have permissions set to `all` (i.e. read and write) and the user `public` (i.e. the general public) has only read permission.
 
    <img class="screen-shot" src="/static/images/eml-list-of-allow-3-users.png" width="70%">

## Changing permissions

To change permissions, the EML metadata will need to be modified using one of the following approaches:

### ezEML

1. Login to your ezEML account.
2. [Fetch the data package from the EDI data repository](https://ezeml.edirepository.org/static/user_guide/fetch.pdf).
3. Go to the Data Package ID page, and increment the data package [version number](/templates/resources/the-data-package#data-package-identifier) by 1.
4. Download the EML file.
5. Open the EML file in a text editor.
6. Search for the `<access>` element.
7. Each `<allow>` element nested within `<access>` represents a user ID and the associated permissions. In the example below, the users `EDI` and `sbashevkin` have permissions set to `all` (i.e. read and write) and the user `public` (i.e. the general public) has only read permission.
 
    <img class="screen-shot" src="/static/images/eml-list-of-allow-3-users.png" width="70%">
   
8. To add a new user `dbosworth` with `all` permissions, simply copy and paste an existing `<allow>` element and modify the `uid` to `dbosworth` and the permission to `all`. The revised `<access>` element should look like the following:
 
    <img class="screen-shot" src="/static/images/eml-list-of-allow-4-users.png" width="70%">
   
9. To remove a user, delete the `<allow>` element for that user.
10. Save the file.
11. Proceed to the publishing section below.

### EMLassemblyline

Add multiple users to the access control rules via the `user.id` parameter of the `make_eml()` function. For more information, see the associated [documentation](https://ediorg.github.io/EMLassemblyline/reference/make_eml.html).

## Publishing updates

In order for the changes to take effect, the revised EML metadata will need to be uploaded to the EDI Data Portal. For more information see the section on [publishing edited data and metadata](/templates/resources/updating-a-data-package#publishing-edited-data-and-metadata).



