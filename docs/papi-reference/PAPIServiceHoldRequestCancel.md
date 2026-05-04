# HoldRequestCancel

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestCancel.htm_

You are here:

## HoldRequestCancel

Cancel a single hold request or all hold requests for a specific patron.

You can cancel the following hold statuses:

- 1 - inactive

- 2 - active

- 4 - pending

- 7 - not supplied

- 18 - located

If the library enables it, you can also cancel hold requests with the following statuses:

- 5 - shipped

- 6 - held

**Note**:
Submitting a zero for the RequestID forces a "cancel all" operation.

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

ID of workstation calling this method

|
|

userid

|

>0

|

Yes

|

ID of user calling this method (not patron ID)

### XML Elements Returned

The following XML elements are returned following the cancel request.

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

SysHoldRequestID

|

ID of the canceled hold request.

|
| ReturnCode
|

Return code
0 - Success
-1 - Failure

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/holdrequests/803425/cancelled?wsid=1&userid=1

### Return - Success

|
|

HTTP/1.1 200 OK

<HoldRequestCancelResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</HoldRequestCancelResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<HoldRequestCancelResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid workstation ID.

</ErrorMessage>

</HoldRequestCancelResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0