# API Documentation

## Version: 1.0

### /v1/data/{queryId}

#### GET

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| queryId | path |  | Yes | string |
| page | query |  | No | long |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | A successful response. | [queryGetDataResponse](historical-data.md#querygetdataresponse) |
| 400 | Invalid Request. |  |
| 403 | Token Expired. |  |
| 404 | Returned when the resource does not exist. |  |

### /v1/data/{queryId}/next

#### GET

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| queryId | path |  | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | A successful response. | [queryGetDataResponse](historical-data.md#querygetdataresponse) |
| 400 | Invalid Request. |  |
| 403 | Token Expired. |  |
| 404 | Returned when the resource does not exist. |  |

### /v1/query

#### POST

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| body | body |  | Yes | [queryPostQueryWithPropertiesRequest](historical-data.md#querypostquerywithpropertiesrequest) |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | A successful response. | [queryGetQueryResponse](historical-data.md#querygetqueryresponse) |
| 400 | Invalid Request. |  |
| 403 | Token Expired. |  |
| 404 | Returned when the resource does not exist. |  |

### /v1/query/{applicationName}

#### GET

**Parameters**

| Name | Located in | Description | Required | Schema |
| :--- | :--- | :--- | :--- | :--- |
| applicationName | path |  | Yes | string |

**Responses**

| Code | Description | Schema |
| :--- | :--- | :--- |
| 200 | A successful response. | [queryGetQueryResponse](historical-data.md#querygetqueryresponse) |
| 400 | Invalid Request. |  |
| 403 | Token Expired. |  |
| 404 | Returned when the resource does not exist. |  |

### Models

#### queryGetDataResponse

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| data | \[ [querySysLogMessage](historical-data.md#querysyslogmessage) \] |  | No |

#### queryGetQueryResponse

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| queryId | string |  | No |
| info | \[ [queryQueryInfo](historical-data.md#queryqueryinfo) \] |  | No |
| errors | \[ [queryQueryErrors](historical-data.md#queryqueryerrors) \] |  | No |

#### queryPostQueryWithPropertiesRequest

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| applicationNames | string |  | No |
| pageSize | long |  | No |
| startTime | string |  | No |
| endTime | string |  | No |
| requestType | [queryRequestType](historical-data.md#queryrequesttype) |  | No |

#### queryQueryErrors

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| Key | string |  | No |
| message | string |  | No |

#### queryQueryInfo

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| Key | string |  | No |
| message | string |  | No |

#### queryRequestType

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| queryRequestType | string |  |  |

#### querySysLogMessage

| Name | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| ID | double |  | No |
| AppName | string |  | No |
| Facility | double |  | No |
| FacilityString | string |  | No |
| Hostname | string |  | No |
| Message | string |  | No |
| MsgID | string |  | No |
| PartitionID | double |  | No |
| Priority | double |  | No |
| ProcID | string |  | No |
| Sender | string |  | No |
| Severity | double |  | No |
| SeverityString | string |  | No |
| StructuredData | string |  | No |
| Tag | string |  | No |
| Timestamp | string |  | No |

