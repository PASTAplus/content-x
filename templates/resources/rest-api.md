# The REST API

The [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html) offers solutions for programmatically interacting with the EDI Data Repository. For any functionality that can be manually handled in the EDI Data Portal (evaluating, uploading, searching, etc.), there is a corresponding REST API operation that can be used to automate the process.

The API is divided into two main categories. The [Data Package Manager API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html) consists of operations involved with publishing and accessing data packages. The [Audit manager API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/audit_manager_api.html) is used to create and provide access to user Audit logs. The API documentation contains all the information to start using the API operations.

For users who prefer to work in an R environment, the [EDIutils R package](https://docs.ropensci.org/EDIutils/index.html) is a client wrapping the REST API that offers all the API operations as R functions. 
