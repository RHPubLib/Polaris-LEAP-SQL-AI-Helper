# Synch_BibReplacementIDGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_BibReplacementIDGe.htm_

You are here:

## Synch_BibReplacementIDGet

This method returns a list of bibliographic record ID replacements based on a specified start date. It will return up to 60 days of change data. If internal Polaris bibliographic record IDs are stored outside of the Polaris database, this method will help keep external data synchronized with the Polaris database when bibliographic record IDs change.

Bibliographic record IDs may be replaced in several circumstances. For example, a brief MARC record may be created for a title that does not exist in the catalog. Later, a more descriptive record may be imported. The old record is overlaid with the new record and the underlying internal bibliographic record ID is changed. As another example, when new items are received for an existing bibliographic record, the process may overlay the existing bibliographic record and change the underlying bibliographic record ID if new MARC data is supplied.

**Important: **This method builds a data set based on Polaris transactions data. The transactions **Bibliographic record deleted**, **Bibliographic record created**, and **Bibliographic Record marked for deletion** must be logged. In Polaris Administration, open the system-level database table **Transaction Logging** to verify that these transactions are set to be logged.

A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/AccessToken}/synch/bibs/replacementids?startdate={startdate}
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

startdate

|

YYYY-mm-dd

|

Yes

|

Start date of bibliographic record ID replacements

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

BibReplacementIDRows

|

List of replacement ID rows

|
|

BibReplacementIDRow

|

Container for replacement data

|
|

OriginalBibRecordID

|

Bib record ID that has been replaced

|
|

NewBibliographicRecordID

|

Bib record ID that replaced the original ID

|
|

ReplacementDate

|

Date the overlay occurred

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6TQ
HPGsy1tlZPr/synch/bibs/replacementids?startdate=2012-02-01

### Return

|
|

HTTP/1.1 200 OK

<BibReplacementIDGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<BibReplacementIDRows>

<BibReplacementIDRow>

<OriginalBibRecordID>20790</OriginalBibRecordID>

<NewBibliographicRecordID>793031</NewBibliographicRecordID>

<ReplacementDate>2012-02-13T12:10:10</ReplacementDate>

</BibReplacementIDRow>

<BibReplacementIDRow>

<OriginalBibRecordID>601531</OriginalBibRecordID>

<NewBibliographicRecordID>793032</NewBibliographicRecordID>

<ReplacementDate>2012-02-13T12:14:10</ReplacementDate>

</BibReplacementIDRow>

<BibReplacementIDRow>

<OriginalBibRecordID>793031</OriginalBibRecordID>

<NewBibliographicRecordID>793032</NewBibliographicRecordID>

<ReplacementDate>2012-02-13T12:14:11</ReplacementDate>

</BibReplacementIDRow>

</BibReplacementIDRows>

</BibReplacementIDGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0