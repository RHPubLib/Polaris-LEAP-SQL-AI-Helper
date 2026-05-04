# PatronAccountDeleteTitleList

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronAccountDeleteTitleList.htm_

You are here:

## PatronAccountDeleteTitleList

Deletes the specified existing named title list on the patron account.

|
|  
| DELETE
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patronaccountdeletetitlelist?list={list_id}
|  

### Authorization required?

Yes

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

PatronBarcode

|

Yes

|

Barcode of patron

|
| list
| Yes
| Unique identifier for the list

### Query String Parameters

|
|

Name

|

Required

|

Description/Notes

|
|

list

|

Yes

|

 

### XML Elements Returned

The following XML elements are returned.

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

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/patronaccountdeletetitlelist?list=700

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronAccountDeleteTitleListResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

</PatronAccountDeleteTitleListResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronAccountDeleteTitleListResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage>Record store '999' not found.</ErrorMessage>

</PatronAccountDeleteTitleListResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0