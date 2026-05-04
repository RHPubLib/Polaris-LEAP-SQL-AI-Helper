# RequestsUpdateStatus

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceUpdateRequestStatus.htm_

You are here:

## RequestsUpdateStatus

This protected method will update the request status.

**Important:** A call to AuthenticateStaffUser is required before calling any protected method. Patron blocks are de-duplicated on creation. Duplicate blocks are not allowed.

|
|  
| PUT
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{access_token}/circulation/requests/{request_id}/status?action={status_action}
|  

### PAPI Error Codes Unique to This Method

|
| PAPI
Error Codes
|

Description

|
|

-4003

|

Invalid request ID specified

|
|

-4407

|

Request status invalid for this process

|
|

-4408

|

Invalid request status change requested

|
|

-4409

|

Invalid hold user not supplied reason

|
|

-4410

|

This is the only item available for the hold

|
|

-4411

|

No other items are available to fill the hold

### Authorization required?

Yes

### Protected method

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

RequestID

|

Yes

|

The request being acted upon

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
| action
|

Yes

|

Valid actions include:

deny = Deny request

locate = Sets the request status to located.

return = Sets the request status to pending if the request has been set to located in error.

askmelater = Submits the hold request to the askmelater process.

|
| itemid
| Conditionally
| The ItemRecordID of the item bound to the request. The value is required for the following actions: locate, return, askmelater

|
| denyreason
| Conditionally
| The ReasonID from the table HoldUserNotSuppliedReasons. This value is required for the “deny” action.

### XML Elements Returned

The following XML elements are returned.

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

### Body

N/A

### Locate Example

|
|

http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/circulation/requests/12345/status?action=locate&
itemid=4527

### Return Example

|
|

http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/ circulation/requests/12345/status?action=return&
itemid=4527

### Ask Me Later Example

|
|

http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/ circulation/requests/12345/status?action=
askmelater&itemid=4527

### Deny Example

|
|

http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/ circulation/requests/12345/ status?action=deny&
denyreason =4527

### Return

|
|

<PAPIResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PAPIResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0