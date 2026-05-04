# CollectionsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceCollectionsGet.htm_

You are here:

## CollectionsGet

Returns a list of collections based on the organization ID. Branches utilize a subset of collection information maintained at the system level in Polaris. To retrieve a list of all collections in the system, pass in an organization ID of 1. To retrieve a list of collections for a specific branch, pass in the branch ID.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/collections
|  

### Authorization required?

Yes

### XML Elements Returned

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
|

ID

|

ID of collection

|
|

Name

|

Display name of collection

|
|

Abbreviation

|

Collection abbreviation

### Example

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/collections

http://localhost/PAPIService/REST/public/v1/1033/100/3/collections

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0