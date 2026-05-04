# PickupBranchesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronPickupBranchesGet.htm_

You are here:

## PickupBranchesGet

Returns a list of valid pickup branches based on the organization ID. The passed-in organization ID is typically the registered branch of the patron placing a hold request or changing the pickup location of an existing request. The endpoint returns a list of branch-level organization IDs.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/pickupbranches
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
| ID
| Pickup branch organization ID.

### Return - Success

|
|

HTTP/1.1 200 OK

<PickupBranchesGetResult>

<PAPIErrorCode>5</PAPIErrorCode>

<ErrorMessage>string</ErrorMessage>

<PickupBranchesRows>

<ID>1</ID>

<ID>3</ID>

<ID>4</ID>

<ID>7</ID>

<ID>8</ID>

</PickupBranchesRows>

</PickupBranchesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0