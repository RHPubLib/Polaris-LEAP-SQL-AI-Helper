# Synch_BibsByIDGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_BibsByIDGet.htm_

You are here:

## Synch_BibsByIDGet

This method returns a list of bibliographic record IDs and a MARC XML representation of the bibliographic record(s) requested by the user. The specific bibliographic records returned by this method may be queried using a single bibliographic record ID, a comma-delimited list of IDs, or by specifying a range. For example:

- Individual bibliographic record query: **?bibids=243**

- Comma-delimited query: **?bibids=243,253,657,2980,32,35**

- Ranged query: **?bibids=243-280**

**Note:** Query types cannot be combined in a single query. An individual or comma-delimited query must be made separate from a ranged query.

Documentation for the MARC XML schema may be found at the Library of Congress:
**http://www.loc.gov/standards/marcxml/**

**Important:** No more than 50 bibliographic records may be requested at a time. Bibliographic record IDs must be numeric. If a bibliographic record requested does not exist, a row will not be returned. A call to AuthenticateStaffUser is required before calling any protected methods.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/bibs/MARCXML?bibids={BibIDList}
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

bibids

|

Integer

|

Yes

|

Bibliographic record IDs

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
|

GetBibsByIDRows

|

List of bibliographic record IDs and MARCXML records.

|
|

GetBibsByIDRow

|

Container for data.

|
|

BibliographicRecordID

|

Bib record ID of the record.

|
|

BibliographicRecordXML

|

An HTML Encoded representation of MARCXML data. Important: The character coding scheme is Unicode.

|
|

IsDisplayInPAC

|

Boolean true or false. Indicates if the library wishes the record to display in PAC.

|
|

CreationDate

|

The date and time that the record was created in the system.

|
|

FirstAvailableDate

|

The first available date for the bib is the first day the first item linked to the bib becomes available for circulation. This data can be NULL.

|
|

ModificationDate

|

The date and time of last record modification. This data may be NULL.

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7
MXZuJYREw6TQHPGsy1tlZPr/synch/bibs/ MARCXML?bibids=1,5,7,9,11

### Return

|
|

HTTP/1.1 200 OK

<GetBibsByIDResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<GetBibsByIDRows>

<GetBibsByIDRow>

<BibliographicRecordID>1</BibliographicRecordID>

<BibliographicRecordXML>

<marc:collection xsi:schemaLocation="http://www.loc.gov/MARC21/slim

http://www.loc.gov/standards/marcxml/schema/MARC21slim.xsd"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xmlns:marc="http://www.loc.gov/MARC21/slim">

<marc:record>

<marc:leader>|||||cama22||||| a 4500</marc:leader>

<marc:controlfield tag="001">16</marc:controlfield>

<marc:controlfieldtag="005">20091119153925.0
</marc:controlfield>
<marc:controlfieldtag="008">770331s1977 nyua j 000 1 eng u</marc:controlfield>

<marc:datafield tag="010" ind1=" " ind2=" ">

<marc:subfield code="a"> 77005747</marc:subfield>

<marc:subfield code="z">02894080</marc:subfield>

</marc:datafield>

...

<marc:datafield tag="999" ind1=" " ind2=" ">

<marc:subfield code="b">JP Fict Cha</marc:subfield>

<marc:subfield code="c">0</marc:subfield>

<marc:subfield code="g">0</marc:subfield>

<marc:subfield code="h">0</marc:subfield>

<marc:subfield code="i">2</marc:subfield>

<marc:subfield code="j">15</marc:subfield>

<marc:subfield code="k">0</marc:subfield>

<marc:subfield code="x">JP Fict Cha</marc:subfield>

</marc:datafield>

</marc:record>

</marc:collection>

</BibliographicRecordXML>

<IsDisplayInPAC>true</IsDisplayInPAC>

<CreationDate>2009-07-28T11:57:09.347</CreationDate>

<FirstAvailableDate>2009-07-28T11:57:09.347</FirstAvailableDate>

<ModificationDate>2009-07-28T11:57:09.347</ModificationDate>

</GetBibsByIDRow>

</GetBibsByIDRows>

</GetBibsByIDResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0