# BibGetByType Version 2

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceBibGetByType_v2.htm_

You are here:

## BibGetByType Version 2

Returns bibliographic information for a specified item's key and type of key.

For Element IDs ISBN (6) and UPC (48), PAPI checks the Title Display: Configure system administration setting for the full monograph to determine which entities to display. Libraries must ensure that the ISBN (Long) or the UPC (Long) entity is in one of the following lists to have PAPI display the monograph:

-

Available entities

-

Entities for display

### URI

|
|  
| GET
| /public/1 v2/{LangID}/{AppID}/{OrgID}/bib/{key}?type=barcode
|  

### Authorization Required?

Yes, if authentication level set to ALL.

### XML Elements Returned

|
| Name
|

Description/Notes

|
| PAPIErrorCode
|

PAPI Error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

ElementID

|

Is the element identifier. Possible values include:

2 - Publisher
3 - Description
5 - Edition
6 - ISBN
7 - System Items Total
8 - Current Holds
9 - Summary
10 - Local Items Total
11 - Control Number
13 - Call Number
15 - Local Items Available
16 - System Items Available
17 - Format
18 - Author
19 - Series
20 - Subject
21 - Added Author
22 - Added Title
23 - LCCN
24 - ISSN
25 - Other Number
27 - Genre
28 - Notes
29 - Contents
30 - Publisher Number
33 - Web Link
34 - Uniform Title
35 - Title
36 - Volume
37 - Frequency
39 - Former Title
40 - Later Title
41 - STRN
42 - GPO Item Number
43 - CODEN
44 - Target Audience
46 - Medium
48 - UPC

|
|

Occurrence

|

The occurrence of an element. The occurrence of a given element matches the relative order of the underlying data in the MARC record.

|
|

Label

|

The label associated with the element in the language specified by the LanguageID input parameter.

|
|

Value

|

The value of the element to be used for display purposes.

|
|

Alternate

|

A flag that indicates whether this row contains an alternate graphic representation associated with closest preceding row where the Alternate value equals zero. If this flag is set to one, then the value originated from an 880 tag.

**Note**: If an 880 tag is not linked via $6 to a specific data field instance then the Alternate flag will be set to zero.

### Remarks

The properties Local Items Total (10) and Local Items Available (15) will not be included in the returned rowset if the organization identifier is set to system (1).

### Example

|
| http://localhost/PAPIService/REST/public/v2/1033/100/1/bib/5000?type=barcode

### Return - Success

|
|

HTTP/1.1 200 OK

<BibGetByTypeResult xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<BibGetByTypeRows>

<BibGetByTypeRow>

<ElementID>18</ElementID>

<Occurence>1</Occurence>

<Label>Author:</Label>

<Value>Grahame, Kenneth, 1859-1932.</Value>

<Alternate>false</Alternate>

</BibGetByTypeRow>

...

<BibGetByTypeRow>

<ElementID>16</ElementID>

<Occurence>1</Occurence>

<Label>System Items Available:</Label>

<Value>3</Value>

<Alternate>false</Alternate>

</BibGetByTypeRow>

</BibGetByTypeRows>

</BibGetByTypeResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<BibGetByTypeResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Invalid Barcode Supplied</ErrorMessage>

<BibGetRows i:nil="true"/>

</BibGetByTypeResult>

### Error Messages

|
Code
Description

|
| -6
| Invalid type supplied

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0