# Synch_GetDeletedBibs

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_GetDeletedBibs.htm_

You are here:

## Synch_GetDeletedBibs

This method returns a list of bibliographic record IDs for records that have been deleted since a specified date and time. If the library does not retain deleted records, you cannot use this method.

**Important:** This method provides a list of bibliographic records that have been deleted in the Polaris ILS. The method has a date and time parameter. If the time element is not specified, midnight of the day specified is assumed. The returned data contains a generic BibIDListGetResult XML structure (see below).

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/deleted?deletedate={deletedate}
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

Start date and time (records that have been deleted since this date/time).

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

List of Bibliographic record IDs

|
|

BibIDListRow

|

Container for data

|
|

BibliographicRecordID

|

The Bibliographic Record ID

### Example

|
|

https:/[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZu
JYREw6TQHPGsy1tlZPr/synch/bibs/deleted?deletedate=12/2/2011 13:00:00

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