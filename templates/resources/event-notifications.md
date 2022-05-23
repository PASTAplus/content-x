# Event Notifications

The EDI Event Notification Service allows data users to stay on top of changes in the EDI Repository. For example, users can receive notification when a new data package is uploaded or when an existing data package is updated. Such information helps researchers using data from the EDI Repository keep their science up-to-date.

[TOC]

## Requirements

* Event notifications are only accessible to EDI account holders. Authentication with Google, ORCID, or GitHub does not grant access to this service.
* Event notifications are sent as HTTP POST requests, thus requiring the user to have access to a web server capable of receiving the request and then parsing the notification and executing a subsequent process (e.g. workflow).

## Components

Event notifications have two parts: a subscription and a corresponding notification.

### The subscription

The subscription defines what events to follow and where to send the notification when the event occurs. The create, test, and delete subscription processes outlined below can be performed programmatically using the [EDIutils](https://ediorg.github.io/EDIutils/) R Package or similarly the [REST API](https://pastaplus-core.readthedocs.io/en/latest/doc_tree/about.html).

#### Create a subscription

To create a subscription:

1. Login to the EDI Data Portal

    <img class="screen-shot" src="/static/images/login-portal.png" width="100%">

2. Select TOOLS > Event Subscriptions from the menu.

    <img class="screen-shot" src="/static/images/event-sub-dropdown.png" width="100%">

3. Complete the subscription form

    <img class="screen-shot" src="/static/images/event-sub-form.png" width="100%">

4. In the **Package Id** field add the scope under which new data package uploads should trigger a notification (e.g. knb-lter-cap) or add the data package scope and identifier for which new revisions should trigger a notification (e.g. knb-lter-cap.10).
5. In the **Target URL** field add the web server URL that will receive and process the event notification.
6. Click **Subscribe**. The new subscription will be added to a table at the bottom of the page listing all event subscriptions for this user. 

    <img class="screen-shot" src="/static/images/event-subs.png" width="85%">

#### Test a subscription

To test a subscription (i.e. send a notification to the **Target URL**):

1. Select the **Subscription Id**

    <img class="screen-shot" src="/static/images/event-sub-test.png" width="45%">

2. Click **Test**

#### Delete a Subscription

To delete a subscription:

1. Select the **Subscription Id** to delete

    <img class="screen-shot" src="/static/images/event-sub-delete.png" width="45%">

2. Click **Delete**

The deleted subscription will be removed from the table at the bottom of the page. A deleted subscription can be recreated by re-entering the **Package Id** and **Target URL** information, but the **Subscription Id** will be different.

### The notification

An event notification is sent as an HTTP POST request to the Target URL and carries a payload containing the [data package identifier](/templates/resources/the-data-package.md#data-package-identifier) in the body of the request, and the source URL in the header indicating which [repository environment](/templates/resources/repository-environments.md) the event occurred within. Base of source URLs and their corresponding environment:

* portal.edirepository.org = production
* portal-s.edirepository.org = staging
* portal-d.edirepository.org = development

## Considerations

Some other helpful information about event notifications and lessons learned from using them:

* Notifications are only sent once, so listen carefully! If there's a chance a notification was missed, use the **Test** **Subscription Id** feature to manually resend the notification (see above).
* Beware of processing order when related events occur at the same time. One solution is to manage notifications within a queue to facilitate sequential processing.
* Log messages for diagnostics. Adding process messages to a log file expedites problem solving when issues arise.
* Identify changes in source data packages when the event corresponds to an update. Minor updates to metadata may not merit a full reprocessing of the corresponding source data package.
* Wrap critical processes with error handling and on exit clean up to ensure run completion.
* Email the processing log to project personnel to catch errors and broken runs when they happen.

## Tools

* [listener](https://github.com/EDIorg/ecocomDP-listener) - This web application listens for EDI Event Notifications and places each incoming notification into a queue. The queue is an SQLite database containing attributes of the notification and are marked with a "processed"/"unprocessed" tag.
* [maintainer](https://github.com/clnsmth/maintainer) - This web application builds on the event notification listener by including a workflow manager and static website for research projects. This application maps event notifications to workflows and posts updates in real time to a project website.

## Examples

* ecocomDP-maintainer - Updates [ecocomDP](/templates/resources/thematic-standardization.md#ecocomdp) data packages when their corresponding source data package updates.
* [PASTA Upload Tweeter](https://github.com/EDIorg/pasta-upload-tweeter) - Tweets when a new data package is uploaded to the EDI Data Repository.
