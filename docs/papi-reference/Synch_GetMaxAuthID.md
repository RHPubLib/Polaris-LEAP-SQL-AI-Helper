# Synch_GetMaxAuthID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetMaxAuthID.htm_

You are here:

## Synch_GetMaxAuthID

This method returns the maximum authority record ID.

**Important: **This method provides information for item records that have a “final” status. It returns a generic AuthIDListGetResult XML structure (see below).

A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/maxid
|  

### Authorization required?

Yes

### Protected method?

Yes

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

The authority record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/items/maxid

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