# Synch_GetDeletedAuths

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedAuths.htm_

You are here:

## Synch_GetDeletedAuths

This method returns a list of authority record IDs for records that have been deleted since a specified date and time. If the library does not retain deleted records, you cannot use this method.

Important: This method provides information for authority records that have been deleted in the Polaris ILS.This method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed. This method returns a generic AuthIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/delete
|  

### Authorization required?

Yes

### Protected method?

Yes

### Query String Parameters

|
|

Name

|

Value

|

Required

|

Description/Notes

|
|

deletedate

|

YYYY-MM-DDTHH:MM:SS

|

Yes

|

Start date and time (records that have been deleted since this date/time)

### XML Elements Returned

|
|

Name

|

Description/Notes

|
|

PAPIErrorCode

|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
|

ErrorMessage

| Error or information message

|
|

AuthIDListRows

|

List of item record IDs

|
|

AuthIDListRow

|

Container for data

|
|

AuthorityRecordID

|

The Authority Record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQ
HPGsy1tlZPr/synch/auths/deleted?deletedate=12/2/2011 13:00:00

### Return

|
|

HTTP/1.1 200 OK

<AuthIDListGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<AuthIDListRows>

<AuthIDListRow>

<AuthorityRecordID>807343</AuthorityRecordID>

</AuthIDListRow>

</AuthIDListRows>

</AuthIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0