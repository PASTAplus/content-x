# SAL API Documentation

The **System Activity Logger (SAL)** is a unified, high-level event logger for EDI services, capable of generating meaningful usage reports for both internal operators and end users. Registered users can generate usage reports from SAL to track their EDI activity or resources they own.

[TOC]

## Create Event Log
Endpoint for recording service activity events. Callers stream a JSON body describing the event; the service validates the payload, persists the record, and returns the created log record ID. Create a new event log record. Accepts a JSON request body with required and optional fields. Returns `201 Created` with the created log record ID.

`POST /v1/log`

### Access Control

Write access requires `write` permission on the `sal:access` resource in the EDI IAM service. This permission is granted by an IAM superuser on a per-group basis. See the project README for setup details.

### Parameters

| Parameter | In           | Required | Description                                           |
|-----------|--------------|----------|-------------------------------------------------------|
| `token`   | Query string | Yes*     | JWT bearer token. Either `token` or `key` is required |
| `key`     | Query string | Yes*     | API key. Either `token` or `key` is required          |
| (body)    | Request body | Yes      | JSON object describing the event (see fields below)   |

### Request Body Fields

| Field        | Required | Description                                                            |
|--------------|----------|------------------------------------------------------------------------|
| `created_at` | No       | Timestamp of when the event was created (e.g., `2024-06-01T12:34:56Z`) |
| `service`    | Yes      | Name of the EDI service generating the event (e.g., `pasta`)           |
| `method`     | Yes      | Name of the service method or operation being logged                   |
| `context`    | No       | Additional context key/values for the event                            |
| `resource`   | No       | The resource identifier involved in the event                          |
| `user_agent` | No       | User-agent string of the originating client                            |
| `referrer`   | No       | Referrer URL of the originating request                                |
| `ip_address` | No       | IP address of the originating client                                   |
| `edi_ids`    | No       | List of EDI-IDs of the end users on whose behalf the event occurs      |

**created_at:** This timestamp should be set only when the event happened at another time than when the call is being made. When not provided by the client, it is set by the server. This allows for consistent event ordering even if the client and server clocks are not perfectly synchronized.

### Response

| Status             | Description                                                              |
|--------------------|--------------------------------------------------------------------------|
| `201 Created`      | Log record created successfully; response body contains the record ID    |
| `400 Bad Request`  | Missing `?key=`/`?token=`, invalid JSON body, or missing required fields |
| `401 Unauthorized` | See [Parameters](parameters.md)                                          |
| `403 Forbidden`    | Caller does not have `write` permission on `sal:access`                  |

**`201 Created` response body:**

| Field    | Description                         |
|----------|-------------------------------------|
| `method` | API method name (`createEventLog`)  |
| `msg`    | Human-readable confirmation message |
| `id`     | Integer ID of the new log record    |

### Examples

**Request:**

```shell
curl -X POST "https://<host>/v1/log?key=<api-key>" \
  -H "Content-Type: application/json" \
  -d '{
    "service": "pasta",
    "method": "createDataPackage",
    "resource": "knb-lter-ble.1.1",
    "ip_address": "192.0.2.10"
  }'
```

**Response `201 Created` (JSON):**

```json
{
  "method": "createEventLog",
  "msg": "Log record created",
  "id": 4821
}
```

## Get Event Log Records

Return a filtered list of event log records. All filter fields are optional; omitting them returns records up to `limit`. Results are paginated.

`POST /v1/events`

### Parameters

| Parameter | In           | Required | Description                                           |
|-----------|--------------|----------|-------------------------------------------------------|
| `token`   | Query string | Yes*     | JWT bearer token. Either `token` or `key` is required |
| `key`     | Query string | Yes*     | API key. Either `token` or `key` is required          |

All filter and pagination fields are passed as a **JSON request body** (all optional):

| Field           | Type    | Description                                                           |
|-----------------|---------|-----------------------------------------------------------------------|
| `id`            | integer | Filter by log record ID                                               |
| `service`       | string  | Filter by service name (e.g. `pasta`)                                 |
| `method`        | string  | Filter by method name (e.g. `createDataPackage`)                      |
| `context`       | dict    | Filter by JSONB containment — all provided key/value pairs must match |
| `resources`     | list    | Filter by resource identifiers (matches any provided value)           |
| `resource_type` | string  | Filter by parsed resource type (`ARCHIVE`, `DATA`, etc.)              |
| `scope`         | string  | Filter by parsed package scope value                                  |
| `identifier`    | integer | Filter by parsed package identifier                                   |
| `revision`      | integer | Filter by parsed package revision                                     |
| `entity`        | string  | Filter by parsed package entity value                                 |
| `user_agent`    | string  | Filter by user-agent string                                           |
| `referrer`      | string  | Filter by referrer URL                                                |
| `ip_address`    | string  | Filter by IP address                                                  |
| `edi_ids`       | list    | Filter by logs containing one or more of the provided EDI IDs         |
| `min_lat`       | number  | Filter by minimum latitude (inclusive)                                |
| `max_lat`       | number  | Filter by maximum latitude (inclusive)                                |
| `min_lon`       | number  | Filter by minimum longitude (inclusive)                               |
| `max_lon`       | number  | Filter by maximum longitude (inclusive)                               |
| `city`          | string  | Filter by city name                                                   |
| `region_name`   | string  | Filter by region/state name                                           |
| `country_code`  | string  | Filter by ISO country code                                            |
| `since`         | string  | Include records on or after this datetime (ISO 8601)                  |
| `until`         | string  | Include records before this datetime (ISO 8601)                       |
| `limit`         | integer | Maximum number of records to return (default: `100`)                  |
| `offset`        | integer | Number of records to skip for pagination (default: `0`)               |

### Response

| Status             | Description                                                              |
|--------------------|--------------------------------------------------------------------------|
| `200 OK`           | Log records retrieved successfully                                       |
| `400 Bad Request`  | Invalid date format or other parameter errors                            |
| `401 Unauthorized` | See [Parameters](parameters.md)                                          |
| `403 Forbidden`    | Caller does not have `read` permission on `sal:access`                   |

**`200 OK` response body:**

| Field     | Description                                    |
|-----------|------------------------------------------------|
| `method`  | API method name (`getLogRecords`)              |
| `msg`     | Human-readable confirmation message            |
| `records` | Array of log record objects (see fields below) |

**Log record object fields:**

| Field          | Description                                                    |
|----------------|----------------------------------------------------------------|
| `id`           | Integer log record ID                                          |
| `created_at`   | Log entry timestamp (ISO 8601)                                 |
| `service`      | Originating service name                                       |
| `method`       | Originating service method                                     |
| `context`      | Stored context JSON value (nullable)                           |
| `resource`     | Related resource identifier (nullable)                         |
| `user_agent`   | User-agent string (nullable)                                   |
| `referrer`     | Referrer URL (nullable)                                        |
| `ip_address`   | Originating IP address (nullable)                              |
| `edi_ids`      | Included only for non-restricted callers; otherwise omitted    |
| `lat`          | Latitude of originating IP (nullable)                          |
| `lon`          | Longitude of originating IP (nullable)                         |
| `city`         | City of originating IP (nullable)                              |
| `region_name`  | Region/state of originating IP (nullable)                      |
| `country_code` | Country code of originating IP (nullable)                      |

### Examples

**Request — filter by service with pagination:**

```shell
curl -X POST "https://<host>/v1/events?key=<your-key>" \
  -H "Content-Type: application/json" \
  -d '{"service": "pasta", "since": "2026-01-01T00:00:00Z", "limit": 25, "offset": 0}'
```

**Response `200 OK` (JSON):**

```json
{
  "method": "getLogRecords",
  "msg": "Log records retrieved",
  "records": [
     {
           "id": 1,
           "created_at": "2001-01-01T00:00:00Z",
           "service": "testservice4",
           "method": "deleteReservation",
           "context": {
                 "category": "info",
                 "entrytext": "d8b28d98aa0f3a055fad550459aa865838ad17e4",
                 "authsystem": "https://pasta.edirepository.org/authentication",
                 "statuscode": 200
             },
           "resource": "https://pasta.lternet.edu/package/data/eml/ecotrends/55/2/45a8fd51aa9e595210579abc4cd94ee2",
           "user_agent": "MATLAB 9.10.0.1602886 (R2021a)",
           "referrer": "https://referrer3.com/",
           "ip_address": "100.101.102.103/32",
           "edi_ids": [
                 "EDI-ae455cc6b88e830fde1e994ac5a11f5cad05b912",
                 "EDI-79a28903fbe33b243eae00320bd4a9900640be0f",
                 "EDI-7bc67e1fc64ee6e389c5b31aeb6c1016cee624d0",
                 "EDI-c40d487422ab7752c4db5a622e13418d68ab80ea",
                 "EDI-78786140ac2a4f71a77d95f1d7c4fe9ce1e0fffc"
             ],
           "common_names": [
                 "test name 704",
                 "test name 167",
                 "test name 231",
                 "test name 777",
                 "test name 667"
             ],
           "lat": -31.648800,
           "lon": -60.708700,
           "city": "Santa Fe",
           "region_name": "Santa Fe",
           "country_code": "AR"
       }
  ]
}
```

For read-count aggregate endpoints, see [Events/Summary](summary.md).
For package-level CSV report endpoints, see [Package Access Report](package.md).


## Get Package Access Report (CSV)

Returns CSV records for PASTA data package resources events.

`POST /v1/events/package`

### Parameters

| Parameter   | In           | Required | Description      |
|-------------|--------------|----------|------------------|
| `key`       | Query string | Yes*     | EDI access key   |
| `edi-token` | Cookie       | Yes*     | JWT token cookie |

\*Either `key` or `edi-token` is required.

Report filters are passed as a **JSON request body**:

| Field           | Type         | Required | Description                                                               |
|-----------------|--------------|----------|---------------------------------------------------------------------------|
| `scope`         | string       | Yes      | Filter by package scope value                                             |
| `identifier`    | integer      | No       | Filter by package identifier                                              |
| `revision`      | integer      | No       | Filter by package revision                                                |
| `resource_type` | list[string] | No       | Filter by resource types (see below). Must be a JSON array when provided. |
| `entity`        | string       | No       | Filter by package entity value                                            |
| `since`         | string       | No       | Start date (`yyyy-mm-dd`, inclusive)                                      |
| `until`         | string       | No       | End date (`yyyy-mm-dd`, inclusive)                                        |

Resource types: **PACKAGE**, **METADATA**, **DATA**, **REPORT**, **ARCHIVE**

### Response

| Status             | Description                                                  |
|--------------------|--------------------------------------------------------------|
| `200 OK`           | CSV report generated successfully                            |
| `400 Bad Request`  | Invalid date range or invalid `since`/`until` date format    |
| `401 Unauthorized` | See [Parameters](parameters.md)                              |
| `400 Bad Request`  | Invalid request body fields (e.g., non-integer `identifier`) |

`200 OK` returns `text/csv` with:

- `Content-Disposition: attachment; filename="package_access_report.csv"`
- Header row for non-restricted callers:
  `id,created_at,service,method,context,resource,user_agent,referrer,ip_address,edi_ids,common_names,lat,lon,city,region_name,country_code`
- Header row for restricted callers:
  `id,created_at,service,method,context,resource,user_agent,city,region_name,country_code`

### Example

**Request — package-level access report for one revision and two resource types:**

```shell
curl -X POST "https://<host>/v1/events/package?key=<your-key>" \
  -H "Content-Type: application/json" \
  -d '{"scope": "edi", "identifier": 42, "revision": 3, "resource_type": ["DATA", "REPORT"]}'
```

**Response `200 OK` (CSV):**

```csv
id,created_at,service,method,context,resource,user_agent,referrer,ip_address,edi_ids,common_names,lat,lon,city,region_name,country_code
1,2001-01-01T00:00:00Z,testservice4,deleteReservation,"{""category"": ""info""}",https://pasta.lternet.edu/package/data/eml/edi/42/3/example.csv,MATLAB 9.10.0.1602886 (R2021a),https://example.test/page,192.0.2.13,"[""EDI-ae455cc6b88e830fde1e994ac5a11f5cad05b912""]","[""Sample Common Name""]",35.6870,-105.9378,Santa Fe,New Mexico,US
```

## Get Data Package Resource Summary

Returns JSON read-count aggregates for PASTA data package resources.

`POST /v1/events/summary`

Returns read-count rows for all resources in one specific package revision when `revision` is
provided, or across all revisions for a package when `revision` is omitted.

### Authentication

The endpoint requires either a `?token=<jwt>` or `?key=<api-key>` query parameter.

### Request body

All fields are JSON body fields.

| Field        | Type    | Required | Description                                 |
|--------------|---------|----------|---------------------------------------------|
| `scope`      | string  | Yes      | Package scope (for example, `edi`)          |
| `identifier` | integer | Yes      | Package identifier                          |
| `revision`   | integer | No       | Package revision; omit for all revisions    |
| `limit`      | integer | No       | Maximum rows to return (default: `100`)     |
| `offset`     | integer | No       | Rows to skip before returning results (`0`) |

### Response

Both endpoints return `application/json`.

### Example

**Request**

```shell
curl -X POST "https://<host>/v1/events/summary?key=<your-key>" \
  -H "Content-Type: application/json" \
  -d '{"scope":"edi","identifier":42,"revision":3,"limit":100,"offset":0}'
```

**Response**

```json
{
  "method": "getEventsSummary",
  "msg": "Event summary records retrieved successfully",
  "events": [
    {
      "resourceId": "https://pasta.example.org/package/eml/edi/42/3",
      "resourceType": "PACKAGE",
      "scope": "edi",
      "identifier": "42",
      "revision": "3",
      "totalReads": "29"
    },
    {
      "resourceId": "https://pasta.example.org/package/metadata/eml/edi/42/3",
      "resourceType": "METADATA",
      "scope": "edi",
      "identifier": "42",
      "revision": "3",
      "totalReads": "67"
    }
  ]
}
```