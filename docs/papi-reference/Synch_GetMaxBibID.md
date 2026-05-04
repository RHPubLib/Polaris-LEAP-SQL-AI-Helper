# Synch_GetMaxBibID

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetMaxBibID.htm_

You are here:

## Synch_GetMaxBibID

This method returns the maximum bibliographic record ID.

**Important: **This method provides information for bibliographic records that have a “final” status. It returns a generic BibIDListGetResult XML structure (see below). A call to AuthenticateStaffUser is required before calling any protected method.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/maxid
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

BibIDListRows

|

List of bibliographic record IDs

|
|

BibIDListRow

|

Container for data

|
|

BibliographicRecordID

|

The bibliographic record ID

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQHPG
sy1tlZPr/synch/bibs/maxid

### Return

|
|

HTTP/1.1 200 OK

<BibIDListGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<BibIDListRows>

<BibIDListRow>

<BibliographicRecordID> 852993 </BibliographicRecordID>

</BibIDListRow>

</BibIDListRows>

</BibIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0