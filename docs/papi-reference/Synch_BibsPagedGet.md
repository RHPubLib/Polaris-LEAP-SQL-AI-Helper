# Synch_BibsPagedGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_BibsPagedGet.htm_

You are here:

## Synch_BibsPagedGet

This method returns a list of bibliographic records in MARC XML representation. The specific bibliographic records returned are in order of bibliographic record id starting with the id after the "lastid" parameter. The number of records returned is specified by the "nrecs" parameter. Documentation for the MARC XML schema is found at the Library of Congress: http://www.loc.gov/standards/marcxml/

The date range specifiers are optional. Both created and modified date ranges may be provided in the same call. A bibliographic record will be included if it matches either of the date ranges.

**Important: **No more than 100 bibliographic records may be requested at a time. Bibliographic record ID specified must be numeric. If a bibliographic record requested does not exist, a row will not be returned.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/MARCXML/paged
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
| lastID
| Use 0 when starting the retrieval process, otherwise, use the last retrieved ID

| No
| The highest Bibliographic Record ID of the last "page" of bibliographic records retrieved. This allows for the current page of records returned to follow sequentially from the previous page retrieved.

|
| nrecs
|  
| No
| The number of records returned.

|
| startdatecreated
|  
| No
| Start date and time of the range of bibliographic records to retrieve by creation date. This is optional. If no date specified, it is assumed to be the beginning of time.

|
| enddatecreated
|  
| No
| End date and time of the range of bibliographic records to retrieve by creation date. This is optional. If no date specified, it is assumed to be the current date and time.

|
| startdatemodified
|  
| No
| Start date and time of the range of bibliographic records to retrieve by modification date. This is optional. If no date specified, it is assumed to be beginning of time.

|
| enddatemodified
|  
| No
| End date and time of the range of bibliographic records to retrieve by creation date. This is optional. If no date specified, it is assumed to be the current date and time.

|
| includeItems
|  
| No
| When retrieving records, include an 852 tag for each item record linked to the bibliographic record.

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
| LastID
| The highest Bibliographic Record ID of the current "page" of bibliographic records retrieved. This is typically used to pass into the next call to this endpoint to retrieve sequential groups of bibliographic records.

|
| BibliographicRecordID
| Internal Polaris numeric identifier of the bibliographic record.

|
| IsDisplayInPAC
| Does this bibliographic record show in public searches in the PAC.

|
| CreationDate
| Date that the bibliographic record was initially cataloged into the Polaris system.

|
| FirstAvailableDate
| The date that at least one item attached to the bibliographic record first becomes available for circulation.

|
| ModificationDate
| The most recent date the bibliographic record was modified.

|
| BibliographicRecordXML
| XML-formatted MARC version of the bibliographic record.

### Example

The following example queries a page of 25 records beginning with bib records after bib id of 19782 that were created after 1/1/2019.

|
|

protected/{Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/MARCXML/paged?
nrecs=25&lastid=19782&startdatecreated=2019-01-01

### Return

|
|

HTTP/1.1 200 OK

<GetBibsPagedResult>

<PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<LastID>1</LastID>

<GetBibsPagedRows>

<BibliographicRecordID>1</BibliographicRecordID>

<IsDisplayInPAC>true</IsDisplayInPAC>

<CreationDate>1970-01-01T00:00:00.001Z</CreationDate>

<FirstAvailableDate>1970-01-01T00:00:00.001Z</FirstAvailableDate>

<ModificationDate>1970-01-01T00:00:00.001Z</ModificationDate>

<BibliographicRecordXML>string</BibliographicRecordXML>

</GetBibsPagedRows>

</GetBibsPagedResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0