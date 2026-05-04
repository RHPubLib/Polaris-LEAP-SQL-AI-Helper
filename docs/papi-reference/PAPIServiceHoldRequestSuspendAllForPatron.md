# HoldRequestSuspendAllForPatron

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestSuspendAllForPatron.htm_

You are here:

## HoldRequestSuspendAllForPatron

Suspend or reactivate all local hold requests for a specific patron whose hold requests have a status of inactive (1), active (2) or pending (4). Uses the same URI as HoldRequestSuspend. Simply passing in a **0** for the RequestID will force a “suspend all” operation.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/holdrequests/0/inactive
|  

|
|  
| PUT
| /public/1/patron/{PatronBarcode}/holdrequests/0/active
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

ID of user calling this procedure.

|
|

ActivationDate

|

Yes

|

Date this hold request will become active.

### XML Elements Returned

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

ID of suspended/reactivated hold request.

|
|

ReturnCode

|

Return code:

0 - Success
-1 - Failure
-4403 - Invalid pickup branch assigned to hold request
-4404 - Error occurred loading SA days to expire

|
|

NewActivationDate

|

Date the system set the hold request to become active.

|
|

NewExpirationDate

|

Date the system set the hold request to expire.

|
|

ErrorMessage

|

Error message

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/holdrequests/0/inactive

### Body

|
|

<HoldRequestActivationData>

<UserID>1</UserID>

<ActivationDate>2009-12-01T00:00:00.00</ActivationDate>

</HoldRequestActivationData>

### Return - Success

|
|

HTTP/1.1 200 OK

<HoldRequestActivationResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<HoldRequestActivationRows>

<HoldRequestActivationRow>

<SysHoldRequestID>803449</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<NewActivationDate>2009-12-31T00:00:00</NewActivationDate>

<NewExpirationDate>2010-05-01T00:00:00</NewExpirationDate>

<ErrorMessage/>

</HoldRequestActivationRow>

<HoldRequestActivationRow>

<SysHoldRequestID>803531</SysHoldRequestID>

<ReturnCode>0</ReturnCode>

<NewActivationDate>2009-12-31T00:00:00</NewActivationDate>

<NewExpirationDate>2010-05-01T00:00:00</NewExpirationDate>

<ErrorMessage/>

</HoldRequestActivationRow>

</HoldRequestActivationRows>

</HoldRequestActivationResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<HoldRequestActivationResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Failed to convert parameter value from a DateTime to Int32.</ErrorMessage>

<HoldRequestSuspendRows/>

</HoldRequestActivationResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0