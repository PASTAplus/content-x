# Self-Publishing

Self-publishing to the EDI repository is reserved for "vetted" users—those authorized to publish data packages without direct oversight. This status reflects a commitment to maintaining the highest standards for data and metadata quality. If you are a first-time publisher, you must collaborate with the EDI Curation Team on your initial submission before transitioning to self-publishing. 

[TOC]

## How to become a "vetted" user

When you sign in to an EDI service (e.g., Data Portal or ezEML), you are using a unique EDI identifier within our software that is linked to the identity provider you used to sign in (i.e., GitHub, Google, Microsoft, or Orcid, or EDI's account service). For you to become a "vetted" user, we need to add this EDI identifier to a special group designated "vetted" so that our authorization service knows you are permitted to publish data packages directly through our publishing interfaces (see [below](/resources/self-publishing#self-publishing-interfaces)). To obtain your EDI identifier, follow these steps:

1. Sign in to our [Identity and Access Management (IAM) service](https://auth.edirepository.org) using your preferred identity provider.
2. From your User Profile page, click on the copy icon &#10697; found at the end of the EDI-ID field just below "Contact."
3. With your copied EDI identifier, paste it into an email and send it to our [support email address](mailto:support@edirepositoyr.org) (support@edirepository.org) with a request explaining that you would like to self-publish your data package.

Once you submit your request, one of our curators will be in touch. If this is your first time working with EDI, we’ll set up a quick video chat to introduce ourselves, answer any questions, and review the best practices for self-publishing. We'll then review your data package and provide feedback on any issues that may arise. If all looks good, we'll add your EDI identifier to the vetted group, and you'll be able to publish your data package directly through our one of our [publishing interfaces](/resources/self-publishing#self-publishing-interfaces).

>Note: At present, EDI supports both a production and staging environment for our users. The staging environment acts as a sandbox for you to test and evaluate your data package before publishing it to the production environment. We highly recommend that you use the staging environment to test your data package before publishing it to the production environment. This helps catch any issues that may arise during the publishing process. To use our staging environment just as you would our production environment, you will need to sign in to the [staging IAM service](https://auth-s.edirepository.org) using the same identity provider you used in step #1 above. This will register your identity in the staging environment, enabling us to add your EDI identifier to the staging "vetted" group. In the near future, EDI will merge the staging and production environments together, eliminating the need to create accounts in both environments.

## Self-publishing interfaces

EDI maintains two user-accessible interfaces for self-publishing. The recommended interface is through the [EDI Data Portal](https://portal.edirepository.org) (and the [staging EDI Data Portal](https://portal-s.edirepository.org)). From the Data Portal home page, select "Login" at the top-right of the page and sign in using the same identity provider as above. Once signed in, navigate to the "Tools&#8594;Evaluate/Upload Data Packages" menu selection and click on the "Choose File" to upload the EML metadata document for your data package. After choosing your file, select either "Evaluate" or "Upload." Evaluate performs a complete review of your data package without the "publishing" step, resulting in a quality report that describes how well your data package meets EDI publishing criteria. Upload performs the review again, but this time, if successful, will publish your data package and assign it a Digital Ojbect Identifier (the staging environment uses *simulated* DOIs).

Alternatively, EDI supports a REST-style [web service API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#upload-and-evaluation) with which you can also self-publish your data package. This is an ideal way to publish data packages in batches or as output from an automated workflow. Like the EDI Data Portal, this API requires you to send your identity information, along with the EML metadata file, in the HTTP request. Because this is an advanced technique, we recommend you contact us at the support email noted above for first-time assistance.

## Self-publishing workflow

Self-publishing data packages with EDI is liberating because you are no longer dependent on the avaialbility of a data curator. It does, however, require more effort on your part because of the increased responsibility for achieving EDI's high standards for data and metadata quality. The steps for self-publishing are similar to those for [pubishing a data package with the EDI Data Curation Team](/resources/resources-for-data-authors#step-1-preparing-for-submission):

1. Prepare your data and metadata (we recommend using [ezEML](/resources/creating-metadata-for-publication#ezeml)).
2. Sign in to one of our staging self-publishing interfaces and evaluate, then upload, your data pacakge.
3. Review the data package "landing page" for errors in metadata formatting or content and, importantly, read the quality report for issues that need to be addressed, including "warnings" that can be easily corrected.
4. Once satisfied with your staging upload, repeat the upload process with our production environment.

_Do not hesitate [contacting EDI](/support/contact-us) if you have any questions or concerns about the self-publishing process or your data package (doing this before attempting to publish your data package in the production environment can prevent lost time and effort)._
