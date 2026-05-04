# BibsPost

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/BibsPost.htm_

You are here:

## BibsPost

Import MARC records to create and overlay bibliographic records in Polaris. An import job is created for each post. By default, Polaris attempts to match the incoming 001 tag to an existing bibliographic record ID. If Polaris finds a match, it modifies the existing record. If Polaris doesn't find a match, it creates a new bibliographic record.

|
|  
| POST
|

/protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{accesstoken}/bibs

|  

### Authorization required?

Yes

### Protected method?

Yes

### URI Parameters

|
|

Name

|

Required

|

Description

|
|

ImportProfileName

|

No

|

Import profile name. If not supplied the default is "PAPI default".

|
| WorkstationID
| No
| Workstation identifier.

### XML Body Elements

Provided in the MARC 21 XML Schema from the Library of Congress, found here:

https://www.loc.gov/standards/marcxml/

### XML Elements Returned

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined in Polaris API - Overview.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message.

|
|

ImportJobID

|

The background import job ID.

### Example

|
| https://localhost/REST/protected/v1/1033/100/1/bibs

### Body

|
|

<collection xmlns="http://www.loc.gov/MARC21/slim">

<record>

<leader>00000nam a22000007i 4500</leader>

<controlfield tag="001">1793091</controlfield>

<controlfield tag="005">20240402112049.0</controlfield>

<controlfield tag="008">211115t20212021nyuaf 000 f eng d</controlfield>

<datafield tag="100" ind1="1" ind2=" ">

<subfield code="a">Tarantino, Quentin</subfield>

</datafield>

<datafield tag="245" ind1="1" ind2="0">

<subfield code="a">Once upon a time in Hollywood</subfield>

</datafield>

</record>

</collection>

### Return - Success

|
|

HTTP/1.1 200 OK

<BibsPostResult>

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<ImportJobID>5814</ImportJobID>

</BibsPostResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<BibsPostResult>

<PAPIErrorCode>-1001</PAPIErrorCode>

<ErrorMessage>Bibliographic import profile name not found</ErrorMessage>

<ImportJobID i:nil="true" />

</BibsPostResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0