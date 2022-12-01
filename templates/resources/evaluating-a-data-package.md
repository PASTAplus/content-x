# Evaluating a Data Package 

Evaluating a data package is key to ensuring that it contains a valid, well-formed EML file that accurately describes the data. Evaluations can be performed manually via the EDI Data Portal, or programmatically using the EDIutils R package or the REST API.

Evaluating a data package requires an [EDI account](/templates/resources/information-manager-quickstart.md#sign-up-for-an-edi-account). Other methods of authentication (e.g. Google, ORCID, GitHub) do not allow evaluation.

To learn more about evaluation and to request new checks, see the [EML Congruence Checker GitHub](https://github.com/EDIorg/ECC).

[TOC]

## EDI Data Portal

To evaluate a data package via the [EDI Data Portal](https://portal.edirepository.org/nis/home.jsp):

### Login

From the Data Portal, click the **Login** button and enter EDI account credentials.

<img class="screen-shot" src="/static/images/login-portal.png" width="95%">

### Evaluating the data package

1. Navigate to the **Evaluate/Upload Data Packages** page: 

    <img class="screen-shot" src="/static/images/eval-upload-dropdown-portal.png" width="95%">

2. **Choose File** - Browse and select the EML file to be evaluated 
3. Unless every data object in the EML file is associated with [static data links](/templates/resources/uploading-with-static-data-links.md), select the checkbox next to **Manually upload data…** to allow manual upload.

    <img class="screen-shot" src="/static/images/evaluate-manual-upload.png" width="95%">

4. From the manual uploads page, choose the files to upload for the data package and click the **Evaluate** button.

    <img class="screen-shot" src="/static/images/evaluate-manual-upload-page.jpg" width="95%">

>Be aware that the length of the evaluation process increases with the size of the data being evaluated. Once the process has begun, the browser window can be closed without interrupting the evaluation. Use the EDI Dashboard [PASTA is Working On](https://dashboard.edirepository.org/dashboard/pasta/render_working_on) feature to see when evaluation has completed. The evaluation report summary and full report can be viewed from the **View Evaluate/Upload Results** page.


### Viewing the evaluation report summary

After the evaluation runs, the **View Evaluate/Upload Results** page will be displayed. This page provides the **Evaluation Report Summary**, the first view of the data package quality.

<img class="screen-shot" src="/static/images/eval-summary-table.png" width="65%">

### Viewing the evaluation report

This summary table also provides a link to the full **Evaluation Report**, which documents the outcome of each evaluation test performed, including the specific areas for improvement noted by **Warn** and **Error** labels.

<img class="screen-shot" src="/static/images/eval-report.png" width="100%">

## EDIutils

To evaluate a data package using the [EDIutils](https://docs.ropensci.org/EDIutils/index.html) R package:

### Login

Use the [`login()`](https://docs.ropensci.org/EDIutils/reference/login.html) function with EDI account credentials.

### Evaluating the data package

Use the [`evaluate_data_package()`](https://docs.ropensci.org/EDIutils/reference/evaluate_data_package.html) function to begin the evaluation process and provide the full path to the EML file and the [repository environment](/templates/resources/repository-environments.md) to evaluate in.

This function returns a "transaction identifier" that is used to reference the evaluation in subsequent function calls. After the evaluation process has begun, pass the transaction identifier to the [`check_status_evaluate()`](https://docs.ropensci.org/EDIutils/reference/check_status_evaluate.html) function to determine if evaluation has completed.

### Viewing the evaluation report summary

Pass the transaction identifier to the [`read_evaluate_report_summary()`](https://docs.ropensci.org/EDIutils/reference/read_evaluate_report_summary.html) function to view the evaluation report summary as plain text.

### Viewing the evaluation report

Pass the transaction identifier to the [`read_evaluate_report()`](https://docs.ropensci.org/EDIutils/reference/read_evaluate_report.html) function, which returns raw XML by default, but will return HTML or text by specifying the `as` parameter.

For a language-agnostic solution, see the REST API documentation for [Evaluate Data Package](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#evaluate-data-package), [Read Data Package Error](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#read-data-package-error), and [Read Evaluate Report](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/pasta_api/data_package_manager_api.html#read-evaluate-report-1).

## Handling warnings and errors

Any evaluation check that results in a warning or error status should be resolved before moving ahead (note that errors must be corrected). Resolve problems with the data and metadata and repeat the evaluation process until all errors (and preferably all warnings) are resolved.

## Interpreting the evaluation report summary

The evaluation report summary is displayed as part of the evaluation process via the EDI Data Portal or can be generated from the EDIutils [`read_evaluate_report_summary()`](https://docs.ropensci.org/EDIutils/reference/read_evaluate_report_summary.html) function.

### Purpose

Provide a quick look at the data package evaluation results. Specifically, the total number of checks run and how many of these checks resulted in statuses of **valid**, **info**, **warn**, or **error**. The meaning of these status messages is as follows:


<table>
  <tr>
   <td><strong>Status</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>Valid
   </td>
   <td>The result of the quality check matches the expectation. Success!
   </td>
  </tr>
  <tr>
   <td>Info
   </td>
   <td>The result of the quality check may or may not match the expectation, but since the expectation is not required, information is returned instead of a Warn or Error. 
   </td>
  </tr>
  <tr>
   <td>Warn
   </td>
   <td>The result of the quality check does not match the expectation. A match is not explicitly required to publish the data package, but strongly recommended.
   </td>
  </tr>
  <tr>
   <td>Error
   </td>
   <td>The result of the quality check does not match the expectation. A match is required before the data package can be published.
   </td>
  </tr>
</table>

## Interpreting the evaluation report

A **Data Package Quality Report**, otherwise known as an **Evaluation Report**, is generated whenever a data package is evaluated or published.

### Structure

The Evaluation Report is typically broken into multiple parts, always starting with the **Dataset Report**, and followed by an entity report for each data object included in the data package.These are differentiated by header lines with the **Entity Name** and **Identifier**.

The Dataset and Entity Reports share the same layout:


<table>
  <tr>
   <td><strong>Report Column Name</strong>
   </td>
   <td><strong>Explanation</strong>
   </td>
  </tr>
  <tr>
   <td>#
   </td>
   <td>The number of the quality check
   </td>
  </tr>
  <tr>
   <td>Identifier
   </td>
   <td>The identifier of the quality check
   </td>
  </tr>
  <tr>
   <td>Status
   </td>
   <td>The status of the result of the quality check
   </td>
  </tr>
  <tr>
   <td>Quality Check
   </td>
   <td>Describes the type of the quality check (data, metadata, or congruency), the system (knb, lter), and the status that results on failure
   </td>
  </tr>
  <tr>
   <td>Name
   </td>
   <td>The name of the quality check
   </td>
  </tr>
  <tr>
   <td>Description
   </td>
   <td>Brief description of the quality check
   </td>
  </tr>
  <tr>
   <td>Expected
   </td>
   <td>The result that the quality check is expecting
   </td>
  </tr>
  <tr>
   <td>Found
   </td>
   <td>The actual result of the quality check
   </td>
  </tr>
  <tr>
   <td>Explanation
   </td>
   <td>Additional information describing the rationale of the quality check
   </td>
  </tr>
  <tr>
   <td>Suggestion
   </td>
   <td>Potential data package improvements to implement to pass the quality check
   </td>
  </tr>
  <tr>
   <td>Reference
   </td>
   <td>Source of the rationale for the quality check or where to find more information
   </td>
  </tr>
</table>



### Interpretation

Parse through the document and address any errors or warnings (denoted by the **Error** and **Warn** labels). To understand why a quality check failed, first read the **Name** and **Description** of the quality check to determine what was being tested and how the test was being conducted. Then, compare the **Expected** result to what was **Found**. If it is still not clear what caused the failure, try to gain additional insight from the **Explanation**, **Suggestion**, and **Reference** fields, or [contact EDI](/templates/support/contact-us.md) for clarification.
