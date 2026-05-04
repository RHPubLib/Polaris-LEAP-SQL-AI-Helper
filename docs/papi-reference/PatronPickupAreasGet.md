# PickupAreasGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronPickupAreasGet.htm_

You are here:

## PickupAreasGet

Returns a list of valid pickup areas for the branch based on the organization ID. The passed-in organization ID is typically the registered branch of the patron placing a hold request or changing the pickup location of an existing request. The endpoint returns a list of branch-level pickup area IDs.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/pickupareas
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

PAPI error code: Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code is populated with a zero.

|
| ErrorMessage
| Error or information message

|
| OrganizationID
| Pickup branch organization ID

|
| PickupAreaID
| Pickup area ID

|
| Description
| Pickup area name

|
| Selected
| Pickup Area is selected, True or False

### Return - Success

|
|

<PickupAreasGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>

</ErrorMessage>

<PickupAreasRows>

<PickupAreasRow>

<OrganizationID>3</OrganizationID>

<PickupAreaID>15</PickupAreaID>

<Description>Lobby</Description>

<SequenceID>1</SequenceID>

<Selected>true</Selected>

</PickupAreasRow>

<PickupAreasRow>

<OrganizationID>3</OrganizationID>

<PickupAreaID>16</PickupAreaID>

<Description>Drive thru window</Description>

<SequenceID>2</SequenceID>

<Selected>true</Selected>

</PickupAreasRow>

<PickupAreasRow>

<OrganizationID>3</OrganizationID>

<PickupAreaID>17</PickupAreaID>

<Description>Hold counter</Description>

<SequenceID>3</SequenceID>

<Selected>true</Selected>

</PickupAreasRow>

</PickupAreasRows>

</PickupAreasGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0