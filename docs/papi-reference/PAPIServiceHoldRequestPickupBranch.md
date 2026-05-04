# HoldRequestPickupBranch

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceHoldRequestPickupBranch.htm_

You are here:

## HoldRequestPickupBranch

This method updates the pickup branch for a hold request when the patron requests the change. The hold request status must be one that is allowed for change requests according to the system-level Polaris Administration setting for the Request parameter **Holds Options - Pickup**. Possible allowed statuses include Active, Held, Inactive, Located, Pending, and Shipped.

|
|  
| PUT
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/holdrequests/{RequestID}/
pickupbranch?userid={user_id}&wsid={workstation_id}&pickupbranchid={pickupbranch_id}
|  

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
| RequestID
| Yes
| ID of the hold request.

|
|

PatronBarcode

|

Yes

|

Barcode of patron.

|
| HoldPickupAreaID
| No
| ID of the hold pickup area. Can be a value of 0, which corresponds to None.

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

wsid

|

Yes

|

ID of the workstation making the endpoint call. This is used in checking if the caller has permission to update the pickup branch.

|
| userid
| Yes
| ID of the Polaris user making the endpoint call. This is used in checking if the caller has permission to update the pickup branch.

|
| pickupbranchid
| Yes
| Internal branch ID that the existing hold request should be change to.

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

### Example

|
|

https://qa-saturn.polarislibrary.com/PAPIService/REST/public/v1/1033/100/1/patron/
12345678/holdrequests/123/pickupbranch?userid=1&wsid=1&pickupbranchid=3

### Return - Success

|
|

HTTP/1.1 200 OK

<PAPIResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PAPIResult>

### Error Message

An invalid request status ID returns the error message **Cannot change pickup branch for request in statusID** (-4016). In addition to any request statuses not allowed due to system administration settings, invalid status IDs include the following:

|
Invalid StatusID
Description

|
| 7
| Not supplied

|
| 8
| Unclaimed

|
| 9
| Expired

|
| 16
| Cancelled

|
| 17
| Out to patron

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0