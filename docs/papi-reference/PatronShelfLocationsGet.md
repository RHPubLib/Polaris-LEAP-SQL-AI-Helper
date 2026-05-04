# ShelfLocationsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronShelfLocationsGet.htm_

You are here:

## ShelfLocationsGet

Returns a list of shelf locations based on the organization ID. Branches utilize a subset of shelf locations. To retrieve a list of all shelf locations in the system, pass in an organization ID of 1. To retrieve a list of shelf locations for a specific branch, pass in the branch ID.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/shelflocations
|  

### Authorization required?

Yes

### Parameters

|
|

Name

|

Description/Notes

|
| orgID
| The organization identifier. This value must be system-level(1) or a branch-level organization identifier.

### XML elements returned

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
| ID
| Pickup branch organization ID.

|
| OrganizationID
| Organization ID of the branch for which you're retrieving the list of shelf locations. A value of "1" returns all shelf locations for the system.

|
| Description
| Description of the shelf location.

### Return - Success

|
|

HTTP/1.1 200 OK

<ShelfLocationsGetResult>

<PAPIErrorCode>1</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<ShelfLocationsRows>

<ID>1</ID>

<OrganizationID>1</OrganizationID>

<Description>string</Description>

</ShelfLocationsRows>

</ShelfLocationsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0