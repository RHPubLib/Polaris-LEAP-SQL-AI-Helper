# PatronSearch

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronSearch.htm_

You are here:

## PatronSearch

This protected method returns a list of patrons that match the search criteria specified in the CCL submitted by the user. Data returned includes the patron’s name, barcode, Polaris Patron ID, and Polaris Organization ID. This method offers query parameters that allow the user to specify the number of patrons, the sort order, and page of data to retrieve.

A call to AuthenticateStaffUser is required before calling any protected method.

See below for a list of valid CCL access points and sort keys for patron records.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/search/patrons/boolean?q={ccl}
|  

### Authorization required?

Yes

### Protected?

Yes

### String Query Values

|
| Name
|

Values

|

Required

|

Description/Notes

|
|

q

|

string

|

Yes

|

Common Command Language (CCL) snippet. Must be URL encoded.

|
|

patronsperpage

|

>0

|

No

|

Maximum number of patrons to return default is 10.

|
|

page

|

>0

|

No

|

Page number Default is 1.

|
|

sort

|

string

|

No

|

CCL specifying the sort order of the return values.

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

|

Error or information message

|
|

WordList

|

A list of the keywords included in the CCL statement.

|
|

TotalRecordsFound

|

The total number of records found that met the search criteria.

|
|

PatronSearchRows

|

A list of patron data

|
|

PatronSearchRow

|

Container for the data row

|
|

PatronID

|

The patron’s ID

|
|

Barcode

|

The patron’s barcode

|
|

OrganizationID

|

The patron’s organization

|
|

PatronFirstLastName

|

The patron’s first and last name

### Example

|
| http://egraham-r2.gisinfosystems.com/PlatoPAPIService/REST/protected/v1/1033/100/1/
aj3TJCD4CeYB8bNFeV5tdiNd1ME37wZt/search/patrons/Boolean?q=EM%3Deric.graham%40polaris
library.com

### Return

|
|

HTTP/1.1 200 OK

<PatronSearchResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage/>

<WordList>eric.graham@polarislibrary.com</WordList>

<TotalRecordsFound>1</TotalRecordsFound>

<PatronSearchRows>

<PatronSearchRow>

<PatronID>356956</PatronID>

<Barcode>eric1234</Barcode>

<OrganizationID>3</OrganizationID>

<PatronFirstLastName>Shaw, Eric C</PatronFirstLastName>

</PatronSearchRow>

</PatronSearchRows>

</PatronSearchResult>

### Patron Access Points

|
|

Access Point

|

Description

|
|

ADCK

|

Address check date

|
|

BD

|

Birth date

|
|

BILL

|

Billed

|
|

BLOCKFT

|

Free text block

|
|

BLOCKLIB

|

Library-assigned block

|
|

EM

|

Email address

|
|

EXD

|

Expiration date

|
|

FAX

|

Fax

|
|

LA

|

Language

|
|

LAD

|

Last activity date

|
|

NOTE

|

Notes

|
|

PATAD

|

Address

|
|

PATB

|

Barcode

|
|

PATC

|

Patron code

|
|

PATL

|

Patron's registered library

|
|

PATN

|

Name

|
|

PATNF

|

Name (First Middle Last)

|
|

PATNL

|

Name (Last, First Middle)

|
|

PHONE

|

Phone

|
|

PREB

|

Former barcode

|
|

PRID

|

Record ID

|
|

REGD

|

Registration date

|
|

STAC

|

Statistical class

|
|

X1

|

Library defined field #1

|
|

X2

|

Library defined field #2

|
|

X3

|

Library defined field #3

|
|

X4

|

Library defined field #4

|
|

X5

|

Library defined field #5

|
|

ZIP

|

Postal code

### Patron Sort Keys

|
|

Access Point

|

Description

|
|

CITY

|

City

|
|

ORG

|

Patron’s Organization

|
|

PATB

|

Barcode

|
|

PATN

|

Name

|
|

PATNL

|

Name (Last, First Middle)

|
|

STATE

|

State

|
|

ZIP

|

Postal code

### Additional CCL Examples

**EM=*polarislibrar* AND PATL=3 AND PATNF=shaw**

|
| EM%3D*polarislibrar*%20AND%20PATL%3D3%20AND%20PATNF%3Dshaw

**EM=eric.graham@polarislibrary.com**

|
| EM%3Deric.graham%40polarislibrary.com

**PHONE=315*652***

|
| PHONE%3D315*652*

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0