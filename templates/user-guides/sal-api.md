# API Documentation for the  Service Activity Logger (SAL)

[TOC]

## Event Log API

The EDI System Activity Logger provides a single write endpoint for recording service activity events. Callers stream a JSON body describing the event; the service validates the payload, persists the record, and returns the created log record ID.

### Access Control

Write access requires `write` permission on the `sal:access` resource in the EDI IAM service. This permission is granted by an IAM superuser on a per-group basis. See the project README for setup details.

---

### Create Event Log

`POST /v1/log`

Create a new event log record. Accepts a JSON request body with required and optional fields. Returns `201 Created` with the created log record ID.

#### Parameters

| Parameter | In           | Required | Description                                           |
|-----------|--------------|----------|-------------------------------------------------------|
| `token`   | Query string | Yes*     | JWT bearer token. Either `token` or `key` is required |
| `key`     | Query string | Yes*     | API key. Either `token` or `key` is required          |
| (body)    | Request body | Yes      | JSON object describing the event (see fields below)   |

#### Request Body Fields

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

#### Response

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

#### Examples

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