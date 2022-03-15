# Quality Assurance

Quality Assurance (QA) is the set of processes or steps taken to ensure data collection is developed and adhered to in a way that minimizes inaccuracies in the resultant data. The purpose of QA is to produce high-quality data while minimizing the need for corrective measures later. Related to QA is the documentation of noteworthy events that may affect interpretation of the data and be important to include with the metadata when the data are published.

[TOC]

## Examples of Quality Assurance

Some examples of QA measures:

* **Calibration** - Is the instrument operating within specification?
* **Operational conditions** - Is the instrument operating within conditions for which it wasn't designed? (e.g. excessive heat)
* **Replication and redundancy** - Facilitates estimation of error and can reduce data gaps (e.g. sample and hardware replication)
* **Anti-fouling** - Minimize data drift (e.g. wipers, manual cleaning)
* **Real-time checks** - Receive alerts when incoming data are out of bounds so adjustments can be made.
* **Schedule and field log** - Remember key events

## Applying Quality Assurance

Consider the parts of the data collection scheme where valuable data are collected and where there is a higher than acceptable likelihood for collection to fail. These fragile parts of the collection scheme could be identified and reinforced to ensure continuous collection of high quality data. Integrating QA into a data collection scheme is facilitated by a process:

1. **Analyze** the data collection scheme and identify important nodes and processes where quality assurance measures can be applied.
2. **Inventory** available resources for allocation (e.g. materials end person hours).
3. **Prioritize** essential components and processes and down weight others.
4. **Allocate** resources according to priorities and formalize operational protocols.

<img src="/static/images/quality-assurance.jpg" width="45%">


Figure: A data collection scheme in which QA measures have been applied (components in orange). QA in this diagram consists of redundant power sources to instrumentation and telemetry, replicate instrumentation and human observers, as well as database backup and value checking.

## Metadata

Some examples of metadata to record during data collection:



* Sampling methodology. List Standardized protocols while noting any potential variation.
* Overview of data collection infrastructure. Only the parts that may affect data values need to be recorded.
* Instrumentation make, mode, accuracy, precision.
* Quality assurance measures implemented and perhaps rationale.
* Deviations from collection protocols and plans.
