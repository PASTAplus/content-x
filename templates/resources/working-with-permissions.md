# Working with Permissions

[TOC]

Permissions determine who can view or modify your published data packages. When you publish a data package with EDI, default access is strictly limited. Only the user who submits the package (designated as the *Owner*) and any subjects or principals explicitly listed in the metadata's access control list are granted permissions. All other users are implicitly denied access.

## Steps

To create or manage resource permissions, follow these steps:

### 1. Sign-in

Sign-in to [IAM](https://auth.edirepository.org) with the identity provider of your choice.

<img class="screen-shot" src="/static/images/IAM-Sign-In.png" width="95%"> 

### 2. Select Permissions

Once signed-in, select *Permissions* and enter the data package identifier you wish to work with into the "Search Packages" form, followed by selecting "Search." You can leave the "Identifier" or "Revision" fields empty as a way to filter your data packages.

<img class="screen-shot" src="/static/images/IAM-Resource-Search.png" width="95%"> 

### 3. Expand Data Package Resource

To inspect a data package's permissions, expand the data package entry in the "Select Resources" panel and check the top selection box to select all items. For example, expanded data package `icarus.13.1` shows that *Owner* permissions are granted exclusively to "Icarus." (Note: While "Public Access" appears in the Set Permissions list, its permission level is set to None.) Next, we will grant "msobol" *Editor* access for this package.

<img class="screen-shot" src="/static/images/IAM-Permissions-View.png" width="95%">

### 4. Add User to Data Package Permissions

In the "Set Permissions" search field, enter "msobol" and select his avatar and EDI identifier. (Note: You can search on a user or group name or EDI identifiers in this field.) This will add "msobol" to the permissions list as a *Reader*. This action will also add "msobol" to the `icarus.13.1` data package permissions under the "Select Resources" panel. Next, select the drop-down menu where *Reader* is displayed and select *Editor*. This will update "msobol" to an *Editor*.

To remove "msobol" (or any other user or group), select the permissions drop-down menu next to their name and select *None*. This will remove them from both the "Select Resources" and "Set Permissions" panel. 

<video class="screen-shot" autoplay loop muted playsinline width="95%">
    <source src="/static/images/IAM-Set-Permissions.webm" type="video/webm">
</video>
