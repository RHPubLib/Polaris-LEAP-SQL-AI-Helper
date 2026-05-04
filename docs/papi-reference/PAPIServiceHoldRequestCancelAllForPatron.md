# HoldRequestCancelAllForPatron

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestCancelAllForPatron.htm_

You are here:

## HoldRequestCancelAllForPatron

Cancel all local hold requests for a specific patron whose hold requests have a status of :

- 1 - inactive

- 2 - active

- 4 - pending

If enabled by the library, hold requests with a status of "5-shipped" can also be canceled.

**Note:** Passing a **0** for the *RequestID* will force a “cancel all” operation.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/holdrequests/{RequestID}/cancelled
|  

### Authorization required?

Yes

### URI Parameters

|
|

Name

|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

Barcode of patron.

|
|

RequestID

|

Yes

|

ID of hold request.

### Query String Parameters

|
| Name
|

Values

|

Required

|

Description/Notes

|
|

wsid

|

>0

|

Yes

|

ID of workstation calling this method.

|
|

userid

|

>0

|

Yes

|

ID of user calling this method (not patron ID).

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

SysHoldRequestID

|

ID of cancelled hold request

|
|

ReturnCode

|

Return code

0 - Success
-1 - Failure

|
|

ErrorMessage

|

Error message if not cancelled

###  

### Example

 

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/holdrequests/0/cancelled?wsid=1&userid=1

###  

### Return - Success

 

|
|

HTTP/1.1 200 OK

<HoldRequestCancelResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<HoldRequestCancelRows>

<HoldRequestCancelRow>

<SysHoldRequestID>803430</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<ErrorMessage/>

</HoldRequestCancelRow>

<HoldRequestCancelRow>

<SysHoldRequestID>803431</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<ErrorMessage/>

</HoldRequestCancelRow>

</HoldRequestCancelRows>

</HoldRequestCancelResult>

###  

### Return - Failed

 

|
|

HTTP/1.1 200 OK

<HoldRequestCancelResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-4300</PAPIErrorCode>

<ErrorMessage/>

<HoldRequestCancelRows/>

</HoldRequestCancelResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0