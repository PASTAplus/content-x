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