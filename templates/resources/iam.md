# The Identity and Access Manager (IAM)

[TOC]

The **Identity and Access Manager (IAM)** is a security framework designed to protect resources across all EDI applications. Built on industry-standard OAuth protocols, IAM integrates directly with identity partners including GitHub, Google, Microsoft, and ORCID.

### Access Control & Profiles

IAM manages access to system and user resources using a straight-forward permission hierarchy: READER, EDITOR, and OWNER.

- **Creating Profiles:** Signing in to [IAM](https://auth.edirepository.org) automatically generates a free profile for you and issues you a unique EDI identifier. This identifier distinguishes you across all EDI applications.
- **Multiple Accounts:** Each profile is linked to a single identity provider account. You can create multiple profiles by signing in with different accounts—even from the same provider.
- **Linking Profiles:** Separate profiles can be linked together to represent a single user, automatically combining the permission sets of all linked profiles into one.

### Additional Capabilities

Beyond simple authentication, IAM provides tools to manage your data and account:

- **Permissions Management:** Directly control who can view or modify your published data packages.
- **User Groups:** Create groups and assign colleagues to streamline permissions across multiple resources at once.
- **Profile Administration:** Update your account details, such as your display name or email address.
- **API Access Keys:** Generate and manage access keys for programmatic interaction and automated API workflows.

<img class="screen-shot" src="/static/images/IAM-Sign-In.png" width="95%"> 

The IAM website is divided into five major sections: **Profile**, **Accounts**, **Groups**, **Memberships**, and **Permissions**, along with a drop-down **Profile menu** from the avatar button at the upper right. Each of these sections and the drop-down menu are described below:

## Profile

The *Profile* page displays information about you, the signed-in user, including your username, EDI identifier (EDI-ID), email address (if set), and whether you have consented to notification by email of relevant information. The important element of this page is the EDI identifier, which can be copied using the copy button (<svg class="icon-char" viewBox="0 0 16 16">
    <path d="M0 6.75C0 5.784.784 5 1.75 5h1.5a.75.75 0 0 1 0 1.5h-1.5a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-1.5a.75.75 0 0 1 1.5 0v1.5A1.75 1.75 0 0 1 9.25 16h-7.5A1.75 1.75 0 0 1 0 14.25Z" />
    <path d="M5 1.75C5 .784 5.784 0 6.75 0h7.5C15.216 0 16 .784 16 1.75v7.5A1.75 1.75 0 0 1 14.25 11h-7.5A1.75 1.75 0 0 1 5 9.25Zm1.75-.25a.25.25 0 0 0-.25.25v7.5c0 .138.112.25.25.25h7.5a.25.25 0 0 0 .25-.25v-7.5a.25.25 0 0 0-.25-.25Z" />
  </svg>) for use in other applications.

<img class="screen-shot" src="/static/images/IAM-Profile.png" width="95%"> 

## Accounts

The *Accounts* page displays your primary profile along with the identity provider used to sign in. It also lists any linked accounts. Account linking lets you combine profiles from different identity providers into a single identity, ensuring seamless access to your data packages no matter how you sign in. You can unlink accounts at any time; however, permissions for specific data packages will remain tied to the primary profile under which they were originally created.

<img class="screen-shot" src="/static/images/IAM-Accounts.png" width="95%"> 

## Groups

The _Groups_ page allows any user with a profile to create and manage user groups for more efficient access control. Instead of granting permissions to individual users one by one—a process that can quickly become cumbersome and error-prone—you can assign permissions directly to a group in a single step. Adding a user to a group immediately grants them access to all resources associated with that group, while removing them revokes that access instantly.

<img class="screen-shot" src="/static/images/IAM-Groups.png" width="95%"> 

## Memberships

The *Memberships* page shows you the groups of which you are a member, and it gives you the option to leave any group by clicking the "Leave" button.  

<img class="screen-shot" src="/static/images/IAM-GroupMembership.png" width="95%"> 

## Permissions

The Permissions page enables you to assign and manage access levels for the resources you own, specifically data packages and their individual components. Permissions can be granted to either an individual user profile or a group across three distinct tiers:

- **Reader** provides read-only access, making it ideal when you want others to view or download your data and metadata without the ability to modify it.
- **Editor** inherits all Reader capabilities and adds the ability to modify the resource, including deleting it or uploading new revisions.
- **Owner** includes full Editor privileges while granting administrative rights to add, modify, or revoke permissions for other users.

_Caution_: Exercise care when granting Editor or Owner privileges, as these allow other users to alter your data or alter who has access to it. 

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

In EDI, access control revolves around three core concepts: Resources, Subjects, and Permissions.

- **Resource:** Any asset that requires protection—specifically data packages or service API methods.
- **Subject:** An entity attempting to interact with a resource, such as a user, group, or software process.
- **Permission:** The authorization level granted to a subject over a resource.

EDI uses a tiered permission structure (mapped to standard read, write, and admin concepts) aligned with our data publishing model:

- **Reader (Read):** Can view or download data packages and execute API service methods.
- **Editor (Write):** Inherits all Reader privileges, plus the ability to create, modify or delete resources.
- **Owner (Admin):** Inherits all Editor privileges, plus the ability to grant or revoke permissions for other subjects.
- **None (Explicit Deny):** A special system level applied exclusively to the Public Access profile to negate all privileges.

How it works in practice: If you are the Owner of a data package, you hold the administrative privilege required to grant another Subject Reader permission, authorizing them to access and download that data. See [here](/resources/create-permissions) for adding permissions to your data packages.

### Working with Groups

In the IAM framework, a Group is a collection of user profiles used to streamline permission management across multiple data packages and individuals.

#### Why Use Groups?

Instead of assigning access rights to individual users repeatedly, you can group users together and assign permissions to the group itself. This significantly simplifies user management:

- **Onboarding:** Adding a new colleague to a group automatically grants them access to all resources assigned to that group.
- **Offboarding:** Removing a user from a group instantly revokes their access across all associated data packages.

#### How They Work

Groups function like individual user profiles and can be assigned any of the standard permission levels (Reader, Editor, or Owner). All members inherit the group’s assigned permissions to perform their work. Constraint: Nesting is not supported—groups cannot be added as members of other groups.

Like individual user profiles, groups can be assigned an API access key and generate an EDI authentication token, allowing them to act as an "authenticated" user within the system.

You can also create _zero-member groups_—groups with no individual users—to serve as a scoped security tool for API access keys in automated scripts or external data catalog integrations. However, to keep your system secure, a zero-member group paired with an access key should never be assigned permissions to data packages or other protected resources. See [here](/resources/keys-and-catalogs) for data catalog best practices.

### Working with Authentication Tokens

Authentication tokens are the mechanism used to convey user profile and group membership information both internally and between applications.

- **For casual users:** The technical details of tokens are not important, and you generally won't need to interact with them.
- **For developers:** If you work directly with EDI's REST APIs, tokens provide necessary profile and group relationship data. Tokens are passed to EDI applications within a *Cookie* header.

#### Technical Considerations

- **Lifespan:** Tokens have a intentionally short (hours) useful lifespan.
- **Best Practice:** For general use with EDI's REST APIs, authentication tokens should be replaced by API Access Keys (detailed below).

Want to dive deeper? If you are a developer looking for technical specifics on our authentication tokens, please contact the EDI team directly to discuss your use case.

### Working with API Access Keys

An API Access Key is a secret identifier used in exchange for an EDI authentication token. It carries the exact same privileges as signing in with your personal identity provider—making it a sensitive credential that must be protected.

#### Key Features and Differences

- **Custom Lifespan:** Unlike authentication tokens (which expire in a few hours and cannot be extended), access key lifespans are defined by you. They default to one year, and you can edit their name and valid date range at any time.
- **Flexible Usage:** Designed primarily for the EDI repository REST API, access keys can also be used to sign in to the Data Portal and the Identity and Access Manager.
- **Multiple Keys:** Registered users can generate multiple keys via the *Profile Menu > Access Keys* page to manage different projects or workflows.

#### How It Works Under the Hood

When you append your access key to an API request as a query parameter (?key=YOUR_KEY), the EDI repository gatekeeper service automatically converts it into a real, short-lived EDI authentication token. The token then handles backend authorization, granting the request the full privileges of your profile.

```https://pasta.lternet.edu/package/eml/icarus/1/1?key=ACCESS_KEY_GOES_HERE```

For step-by-step instructions on generating an API Access Key, see [here](/resources/creating-access-keys).

#### Group Access Keys (Recommended for Security)

To limit security risks—especially when integrating with external data catalogs or automated scripts that only need read access—you can create a Group Access Key instead of a user profile key. See [here](/resources/keys-and-catalogs) for data catalog best practices.

- **Scoped Privileges:** Operates identically to a user key, but its privileges are restricted strictly to what the assigned group is allowed to do.
- **Creation:** Generated from the same *Access Keys* page by selecting a target group instead of your user profile.

_Security Note_: Never share your access keys, post them on public web pages, or commit them into source code repositories.
