# Synch_AuthsByIDGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/Synch_AuthsByIDGet.htm_

You are here:

## Synch_AuthsByIDGet

This method returns a list of authority record IDs and a MARC XML representation of the authority record(s) requested by the user. The specific authorities returned by this method may be specified using a comma-delimited list of authority record IDs.

Documentation for the MARC XML schema may be found at the Library of Congress at: **http://www.loc.gov/standards/marcxml/**

**Important: **No more than 50 authority records may be requested at a time. Authority record IDs must be numeric. If an authority record requested does not exist, a row will not be returned.

A call to AuthenticateStaffUser is required before calling any protected methods.

### URI

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/synch/auths/MARCXML?authids={AuthIDList}
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

AuthIDList

|

Integer

|

Yes

|

Authority record IDs

### XML Elements Returned

|
| Name
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

GetAuthsByIDRows

|

List of authority record IDs and MARCXML records

|
|

GetAuthsByIDRow

|

Container for data

|
|

AuthorityRecordID

|

Authority record ID of the record

|
|

AuthorityRecordXML

|

An HTML Encoded representation of MARCXML data. Important: The character coding scheme is Unicode.

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/protected/v1/1033/100/1/rGhOMQjR7MXZuJYREw6T
QHPGsy1tlZPr/synch/auths/ MARCXML?authids=1,5,7,9,11

### Return

|
|

HTTP/1.1 200 OK

<GetAuthsByIDResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<GetAuthsByIDRows>

<GetAuthsByIDRow>

<AuthorityRecordID>1</AuthorityRecordID >

<AuthorityRecordXML>

<marc:collection xsi:schemaLocation="http://www.loc.gov/standards/marcxml/schema/MARC21slim.xsd"

xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"

xmlns:marc="http://www.loc.gov/MARC21/slim">

<marc:record>

<marc:leader>|||||nza22|||||n 4500</marc:leader>

<marc:controlfield tag="005">20120404203605.0</marc:controlfield>

<marc:controlfield tag="008">000104n| acannaabn |n aaa</marc:controlfield>

<marc:datafield tag="010" ind1=" " ind2=" ">

<marc:subfield code="a">n 00000050</marc:subfield>

</marc:datafield>

<marc:datafield tag="040" ind1=" " ind2=" ">

<marc:subfield code="a">DLC</marc:subfield>

<marc:subfield code="b">eng</marc:subfield>

<marc:subfield code="c">DLC</marc:subfield>

</marc:datafield>

<marc:datafield tag="100" ind1="1" ind2=" ">

<marc:subfield code="a">Pember, Ann,</marc:subfield>

<marc:subfield code="d">1946-</marc:subfield>

</marc:datafield>

<marc:datafield tag="670" ind1=" "ind2=" ">

<marc:subfield code="a">Pember, Ann. Painting close-focus flowers in watercolor, 2000:</marc:subfield>

<marc:subfield code="b">CIP t.p. (Ann Pember) data sheet (b. 04-26-46)</marc:subfield>

</marc:datafield>

</marc:record>

</marc:collection>

</AuthorityRecordXML>

</GetAuthsByIDRow>

</GetAuthsByIDRows>

</GeAuthsByIDResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0