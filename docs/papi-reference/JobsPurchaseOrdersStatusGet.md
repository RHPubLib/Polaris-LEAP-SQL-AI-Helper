# JobsPurchaseOrdersStatusGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/JobsPurchaseOrdersStatusGet.htm_

You are here:

## JobsPurchaseOrdersStatusGet

This jobs endpoint allows you to query the status of your job. Returns only the Polaris user's jobs.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{accesstoken}/jobs/purchaseorders/{jobguid}/status
|  

### Authorization required?

Yes

### Protected method?

Yes

### HTTP Response Codes

The following HTTP Codes are returned.

|
|

Number

|

Description/Notes

|
| 200
|

Success

|
| 401
| Unauthorized

### Job Statuses

|
|

Values

|

Status Description

|
| 1
|

En queued

|
| 2
| Processing

|
| 3
| Succeeded

|
| 4
| Failed

|
| 5
| Scheduled

### Example

|
| https://[hostname]/PAPIService/REST/protected/v1/1033/100/3/iNDUIy7LquAMDji6h2oyacFaLx3RyuM1/jobs/purchaseorders/B3BF63B0-D044-4269-9143-7DEE29B0BB1F/status

### Return - Success

|
|

{

PAPIErrorCode: 0,

ErrorMessage: "",

JobID: "GUID",

JobStatusID: 0,

JobStatusDescription: ""

}

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0