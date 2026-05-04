# Synch_Get UpdatedAuths

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_Get_UpdatedAuths.htm_

You are here:

## Synch_Get UpdatedAuths

This method returns a list of authority record IDs for records that have been updated since a specified date and time.

Important: This method provides information for authority records that have been added or updated in the Polaris ILS. The authority record must have a status of “final.” Updates to the following dates will cause records to appear on this list: Creation date, imported date, modified date, first use date, or record status date.

This method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed.

This method returns a generic AuthIDListGetResult XML structure (see below).

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/updated?updatedate=
{updatedate}
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

updatedate

|

YYYY-MM-DDTHH:MM:SS

|

Yes

|

Start date for record updates

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
sy1tlZPr/synch/auths/updated?updatedate=12/2/2011 13:00:00

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