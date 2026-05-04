# DatesClosedGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceDatesClosed.htm_

You are here:

## DatesClosedGet

This method returns a list of dates closed by organization. If the specified organization ID does not exist, an error is returned (Invalid OrgID supplied, -5000).

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/datesclosed
|  

### Authorization required?

Yes

### XML Elements Returned

Dates closed for the specified organization.

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
| DateClosed
| Date closed

### Example

|
|

https://[HOSTNAME]/PAPIService/REST/public/v1/1033/1/1/datesclosed

### Return - Success

|
|

HTTP/1.1 200 OK

<DatesClosedGetResult xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<DatesClosedRows>

<DatesClosedRow>

<DateClosed>2014-08-03T00:00:00</DateClosed>

</DatesClosedRow>

...

<DatesClosedRow>

<DateClosed>2015-12-25T00:00:00</DateClosed>

</DatesClosedRow>

</DatesClosedRows>

</DatesClosedGetResult>

### Error Message

If the organization ID does not exist in the database, error code -5000 ("Invalid OrganizationID supplied") is returned.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0