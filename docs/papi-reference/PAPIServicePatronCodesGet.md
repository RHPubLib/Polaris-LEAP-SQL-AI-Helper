# PatronCodesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronCodesGet.htm_

You are here:

## PatronCodesGet

This method returns a list of valid patron codes. If the specified organization ID does not exist, an error is returned (Invalid OrgID supplied, -5000).

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patroncodes
|  

### Authorization required?

No

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

org_id

|

Yes

|

Organization ID

### XML Elements Returned

Valid patron codes for the specified organization.

|
|

Name

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
| PatronCodeID
| Patron code ID

|
| Description
| Patron code description

### Example

|
|

https://qa-saturn.polarislibrary.com/PAPIService/REST/public/v1/1033/
100/3/patroncodes

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronCodesGet

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<PatronCodesRows>

<PatronCodesRow>

<PatronCodeID>1</PatronCodeID>

<Description>Regular</Description>

</PatronCodesRow>

...

<PatronCodesRow>

<PatronCodeID>4</PatronCodeID>

<Description>Staff / Board</Description>

</PatronCodesRow>

</PatronCodesRows>

</PatronCodesGet>

### Error Message

If the organization ID does not exist in the database, error code -5000 ("Invalid OrganizationID supplied") is returned.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0