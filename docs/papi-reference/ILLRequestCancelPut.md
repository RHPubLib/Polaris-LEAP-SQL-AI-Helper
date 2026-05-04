# ILLRequestCancelPut

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/ILLRequestCancelPut.htm_

You are here:

## ILLRequestCancelPut

Cancel a single Interlibrary Loan (ILL) request or all ILL requests for a specific patron.

The following hold statuses can be canceled:

- 1 - inactive

- 2 - active

If enabled by the library, hold requests with a status of "5-shipped" can also be canceled.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/illrequests/{illRequestID}/cancelled
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

ILLRequestID

|

Yes

|

ID of ILL request. Passing a 0 for the ILL RequestID will force a “cancel all” operation.

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

**Note:** On successful completion, the PAPI error code is populated with a zero or a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

### Example

#### Single Cancel

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21234000002105/illrequests/5616/cancelled?wsid=1&userid=1

#### Cancel All

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21234000002105/illrequests/0/cancelled?wsid=1&userid=1

 

### Single Cancel - Success

|
|

HTTP/1.1 200 OK

<ILLRequestCancelResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<ILLRequestCancelRows i:nil="true" /></ILLRequestCancelResult>

 

### Cancel All - Success

|
|

<ILLRequestCancelResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance"><PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<ILLRequestCancelRows>

<ILLRequestCancelRow>

<ILLRequestID>7766</ILLRequestID>

<ReturnCode>0</ReturnCode>

<ErrorMessage></ErrorMessage>

</ILLRequestCancelRow>

<ILLRequestCancelRow>

<ILLRequestID>7767</ILLRequestID>

<ReturnCode>0</ReturnCode>

<ErrorMessage></ErrorMessage>

</ILLRequestCancelRow>

</ILLRequestCancelRows>

</ILLRequestCancelResult>

 

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