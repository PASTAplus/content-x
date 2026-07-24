# The Identity and Access Manager (IAM)

[TOC]

The **Identity and Access Manager (IAM)** is a comprehensive security solution for all EDI applications, providing user authentication by building on industry standard OAuth protocols and aligning with identity partners GitHub, Google, Microsoft, and ORCiD. IAM also provides access control management for all system and user resources using simple to understand permission semantics: *READER*, *EDITOR*, and *OWNER*.

As a user, signing in to IAM ([https://auth.edirepository.org](https://auth.edirepository.org)) will create a free *profile* from which a unique EDI authentication token is generated and used to authenticate you to all EDI applications. Each profile is associated with a single identity provider account (e.g., Google, ORCID). You can create multiple profiles by signing in with different identity provider accounts. Accounts may be from the same or different identity providers. Different profiles can be [linked together](/resources/iam#accounts) to represent the same user, combining the permissions from all linked profiles.

IAM, however, provides you much more than just signing in to EDI. IAM allows you to manage the permissions of your published data packages, as well as allowing you to create and assign colleagues to groups for easier permission management. IAM lets you edit your profile properties, like changing your display name or email address. IAM also lets you create API Access Keys, which can be used when accessing the repository API. IAM is the user's Swiss Army Knife when it comes to EDI identity and access management.

<img class="screen-shot" src="/static/images/IAM-Sign-In.png" width="95%"> 

The IAM website is divided into five major sections: **Profile**, **Accounts**, **Groups**, **Memberships**, and **Permissions**, along with a drop-down **Profile menu** from the avatar button at the upper right. Each of these sections and the drop-down menu are described below:

## Profile

The *Profile* page displays information about you, the signed-in user, including your username, EDI identifier (EDI-ID), email address (if set), and whether you have consented to notification by email of relevant information. The important element of this page is the EDI identifier, which can be copied to your browser copy/paste buffer for use in other applications.

<img class="screen-shot" src="/static/images/IAM-Profile.png" width="95%"> 

## Accounts

The *Accounts* page displays the identity provider from which you signed-in—this is your primary profile. This page also shows whether you have any "linked" accounts. Linked accounts allow you to combine profiles generated from different identity providers that represent the same user—you. This is helpful if you actively sign in from different identity providers, but would like manage the same data packages regardless of the identity provider you use. Linked accounts can be "un-linked." However, permissions for data packages will revert back to the primary profile from which they were created.

<img class="screen-shot" src="/static/images/IAM-Accounts.png" width="95%"> 

## Groups

The *Groups* page allows you to create and manage user groups. A group can be created by anyone with a profile. Groups allow you to organize access to your data packages efficiently by granting access to the group in one step, instead of adding users individually, which can become cumbersome and error-prone. Adding a member to a group grants them immediate access to all resources the group has access to, while removing them revokes that access.

"Zero-member" groups, a group without any members, are a strategic tool for use with EDI API Access Keys when deploying program scripts and [external data catalogs](/resources/keys-and-catalogs#1-only-use-zero-member-group-keys). Zero-member groups, however, should never be associated with any data packages or other protected resources when used with an access key.  

<img class="screen-shot" src="/static/images/IAM-Groups.png" width="95%"> 

## Memberships

The *Memberships* page shows you the groups of which you are a member, and it gives you the option to leave any group by clicking the "Leave" button.  

<img class="screen-shot" src="/static/images/IAM-GroupMembership.png" width="95%"> 

## Permissions

The *Permissions* page allows you to apply and manage permissions to resources you own, namely data packages and their components. Permissions grant one of three different levels of access for a user (profile) or group to the resource. These are: "Reader", "Editor", or "Owner." A *Reader* has read-only access to the resource and is ideal for situations where you would like other users to access your data and metadata, without being able to modify it. In addition to read-access, an *Editor* allows a user to modify your resource, including to delete or upload a revision of your data package. An *Owner* has the same permissions as an Editor, but also the rights to add or change permissions for other users. *Be careful when granting Editor and Owner rights to others.* 

<img class="screen-shot" src="/static/images/IAM-Permissions.png" width="95%">

## Profile Menu

The *Profile menu* is accessed by selecting your avatar button near the top-right of the toolbar. The menu itself provides you with four options: **Edit Profile**, **Select Avatar**, **Access Keys**, and **Authentication Token**. 

<img class="screen-shot" src="/static/images/IAM-Avatar.png" width="95%">

- **Edit Profile** - This menu item will allow you to modify attributes of your profile. These include changing your profile visible name, your active email address, and consenting to receive low-volume notification emails from EDI. You may also delete your profile if you desire. This last action will prohibit you from accessing EDI applications that require authentication.
- **Select Avatar** - This menu item will allow you to select available avatars to display on avatar enabled applications. Only avatars associated with your primary and linked profiles are available for selection.
- **Access Keys** - This menu item will allow you to create and manage EDI API Access Keys.
- **Authentication Token** - This menu item will allow you to view and copy your current EDI authentication token.

## Additional Information

### Working with Resource Permissions

Warning, formal definition to follow: *Within EDI, a "resource" is defined as any artifact that requires protection from the actions submitted by a subject, whereas "permissions" convey the level of action a subject may exert onto the resource.* Resources in EDI are data packages or service API methods. Subjects are agents (not AI agents), such as users, groups, or software processes. Permissions, in increasing order of action, are "Reader", "Editor", or "Owner". (A fourth permission, "None", is only used with the "Public Access" user and conveys negation of all privileges). Footnote: The above permissions may be more commonly known as "read", "write", and "all", but "Reader", "Editor", and "Owner" fits well with our data publishing model. A subject who is a Reader, as it sounds, can read a resource (e.g., download data) or execute an API service method. An Editor, in addition to Reader privileges, has the ability to modify a resource (e.g., delete a data package). An Owner, building upon the Editor, can add and remove permissions from other subjects. Putting these concepts together, if you own a data package in EDI, granting another user permission to view it is what gives them access to read that data.

### Working with Groups

Groups within the IAM framework are exactly as they sound: groups are collections of users. See [here](/resources/creating-groups) to create a group. The real benefit of a group shines when you get tired of sharing a repeated number of data packages with an even large number of individual users. Groups make this simple by allowing you to add individuals into the group one time, and then adding the group to the data package's list of privileged subjects. Need to add access to your data packages for a new colleague or staff member? Easy, add them to the group. Someone leaves your research group? Not a problem, remove them from the group. Like individual user profiles, groups can be assigned the same permissions (see above) so that a group member can complete necessary tasks. A couple of important notes about groups: groups cannot be members of other groups and groups, like user profiles, can have an access key assigned to them (see below).  

### Working with Authentication Tokens

Authentication tokens are the essential medium for conveying user profile information between applications and internally within applications. For casual users, the details of an authentication token (see [above](/resources/iam#profile-menu) to view or download your own authentication token) are not important. However, for software developers who work with EDI's REST APIs, the authentication token contains valuable information describing a user's profile and their relationship with groups. For this discussion, it should suffice that authentication tokens have a short useful timespan and their general use with our REST APIs should be replaced with API Access Keys (see below). If you are a developer and would like to learn more about our authentication tokens, please contact EDI directly and we would love to have a chat.

### Working with API Access Keys

An API Access Key is simply a secret that you provide in exchange for your EDI authentication token. Nothing more and nothing less. As simple as this sounds, **access keys are very important and should be treated as sensitive information!** They convey the same privileges you receive when you authenticate to EDI by using your identity provider.

Access keys were primarily designed for use with the EDI repository REST API, but they can also be used on the *Data Portal* and the *Identity and Access Manager* to sign in (bottom of sign-in web page). Using an access is simple, just append it to the end of any EDI repository REST API method as a query parameter using the "key" value attribute. That's it!

```https://pasta.lternet.edu/package/eml/icarus/1/1?key=ACCESS_KEY_GOES_HERE```


As a registered EDI user with a valid profile, you may create any number of access keys to organize and meet your needs. To create an access key, go to the "Profile menu" (see above) and select "Access Keys". The exact steps are described [here](/resources/creating-access-keys). Each access key, when provided in the API method request sent to our repository, is converted to a real EDI authentication token by our repository gatekeeper service. The token is then transferred to the appropriate endpoint service in our repository for further access control processing. This last mile of authentication and authorization is identical to the same steps that occur when you sign in through your identity provider, giving your access key the same privileges of your user profile account. This is why you should never share your access key with another user or expose it in a source code repository or on a web page.

Access keys differ from authentication tokens in another significant way: the valid lifespan of an access key is controlled by you when the access key is created (it defaults to one year), whereas the lifespan for an authentication token is immutable and very short (on the order of hours). Also, once created, you are able to rename your access key and modify the start and end dates of its lifespan.

To reduce the sensitivity of a user profile access key, you can replace it with a "group" access key. A group access key is used exactly the same way as the user profile access key, but only has the privileges given to the group. Group access keys are created on the same "Access Keys" web page described above, selecting the desired group instead of the user profile. We recommend group access keys when your API work does not require higher privileges (data package updates,for example), like the API calls used with external data catalogs. In fact, we have a number of recommendations for how to use access keys with data catalogs [here](/resources/keys-and-catalogs).

