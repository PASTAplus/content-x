# Repository Environments

There are three different environments/tiers in the EDI Data Repository: production, staging, and development. Production is the primary environment where fully published data packages are securely and permanently hosted, staging is used for previewing data packages and testing workflows, and the development environment is used by EDI Repository developers to test new repository features.

<img src="/static/images/repository-tier-earths.jpg" width="75%">
 
Analogous to use of the EDI Data Repository tiers, a worldly deity would  (hopefully) test new features on development and staging Earths before releasing to production.

[TOC]

## Production

The production environment is where data packages are officially and securely published with a DOI and made permanently accessible for reuse. All features of the production environment are mature and stable. The production version of the EDI Data Portal is accessible at [portal.edirepository.org](https://portal.edirepository.org).

## Staging

The staging environment is where new features of the EDI Data Repository mature before release to production, and is used for creating a shareable proof of a data package during [the review process](the-review-process.md), and testing new workflows. The staging version of the EDI Data Portal can be accessed at [portal-s.edirepository.org](https://portal-s.edirepository.org). 

While the staging functions almost exactly as production, there are notable differences. The key differences are that packages published to the staging portal are not assigned a DOI and that landing pages have additional markup to alert users that they are viewing a test version of a package. Furthermore, EDI does not guarantee for data to be available here indefinitely.

## Development

The development environment is used for testing new and, possibly, unstable features of the EDI Data Repository that are not yet mature enough for release to staging. The development version of the EDI Data Portal can be accessed at [portal-d.edirepository.org](https://portal-d.edirepository.org). 

While there is rarely a reason for most users to operate in the development environment, it can be used to test data packages and workflows with the newest features that will eventually be released to production.
