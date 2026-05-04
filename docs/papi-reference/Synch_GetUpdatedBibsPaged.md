# Synch_GetUpdatedBibsPaged

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetUpdatedBibsPaged.htm_

You are here:

## Synch_GetUpdatedBibsPaged

This method returns a list of bibliographic record IDs for records that have been updated since a specified date and time.The paged method allows the retrieval of the ID list in smaller packets.

A date, last record ID, and number of records to return must be specified. When retrieving the first set of records, the "lastid" of 0 forces the process to start at the beginning of the list. Then, when retrieving subsequent records, the "lastid" is used as the starting ID for the next request.

Important: This method provides information for bibliographic records with a “final” status. Updates to the following dates will cause records to appear on this list: Creation date, imported date, modified date, first available date, or record status date.

If the time element is not specified, the date and time parameter will assume midnight of the day specified.

This method returns a generic BibIDListGetResult XML structure (see below).

A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/updated/paged?updatedate=6/5/2017&
lastid=0&nrecs=10
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

|
| lastid

| Use 0 when starting the retrieval process, otherwise, use the last retrieved ID
| Yes
|  

|
| nrecs
| Number of records to return
| Yes
|  

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
sy1tlZPr/synch/bibs/updated/paged?updatedate=6/5/2017&lastid=0&nrecs=10

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

<BibliographicRecordID>803851</BibliographicRecordID>

</BibIDListRow>

</BibIDListRows>

</BibIDListGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0