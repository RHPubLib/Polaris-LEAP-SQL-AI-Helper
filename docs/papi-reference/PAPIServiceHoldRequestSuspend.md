# HoldRequestSuspend

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestSuspend.htm_

You are here:

## HoldRequestSuspend

Suspend or reactivate a single hold request.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/holdrequests/{RequestID}/inactive
|  

|
|  
| PUT
| /public/1/patron/{PatronBarcode}/holdrequests/{RequestID}/active
|  

### Authorization required?

Yes

### URI Parameters

|
| Name
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

### Request Body XML

**Important:** XML elements must be in the order shown below.

|
|

<HoldRequestActivationData>

<UserID/>

<ActivationDate/>

</HoldRequestActivationData>

### XML Body Elements

|
|

Name

|

Required

|

Description/Notes

|
|

UserID

|

Yes

|

ID of user calling this procedure

|
|

ActivationDate

|

Yes

|

Date this hold request will become active

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| SystemHoldRequestID
| ID of suspended/reactivated hold request

|
| ReturnCode
|

Return code

0 - Success
-1 - Failure

|
|

NewActivationDate

|

Date the system set the hold request to become active

|
|

NewExpirationDate

|

Date the system set the hold request to expire

|
|

ErrorMessage

|

Error message

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/217560033
32022/holdrequests/803449/inactive

### Body

|
|

<HoldRequestActivationData>

<UserID>1</UserID>

<ActivationDate>2009-12-31T00:00:00.00</ActivationDate>

</HoldRequestActivationData>

### Return - Success

|
|

HTTP/1.1 200 OK

<HoldRequestActivationResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/><HoldRequestActivationRows>

<HoldRequestActivationRow>

<SysHoldRequestID>0</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<NewActivationDate>2009-12-31T00:00:00</NewActivationDate>

<NewExpirationDate>2010-05-01T00:00:00</NewExpirationDate>

<ErrorMessage/>

</HoldRequestActivationRow>

</HoldRequestActivationRows>

</HoldRequestActivationResult>

### Request - Failed

|
|

HTTP/1.1 200 OK

<HoldRequestActivationResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-4405</PAPIErrorCode>

<ErrorMessage/>

<HoldRequestActivationRows>

<HoldRequestActivationRow>

<SysHoldRequestID>0</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<NewActivationDate>0001-01-01T00:00:00</NewActivationDate>

<NewExpirationDate>0001-01-01T00:00:00</NewExpirationDate>

<ErrorMessage/>

</HoldRequestActivationRow>

</HoldRequestActivationRows>

</HoldRequestActivationResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0