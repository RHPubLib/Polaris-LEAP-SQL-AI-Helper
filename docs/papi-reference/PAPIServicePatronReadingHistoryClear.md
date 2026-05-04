# PatronReadingHistoryClear

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronReadingHistoryClear.htm_

You are here:

## PatronReadingHistoryClear

Clears the historical list of items a patron has checked out. Supplying a list of reading history IDs will remove only the specified historical entries.

|
|  
| DELETE
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/readinghistory
|  

|
|  
| DELETE
| /public/1/patron/{PatronBarcode}/readinghistory?ids={ids}
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

Barcode of patron.

### Query String Parameters

|
| Name
|

Required

|

Description/Notes

|
|

ids

|

No

|

Comma delimited list of reading history IDs. <int>,<int>,<int> Maxiumum of 50 IDs allowed.

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
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
readinghistory

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronReadingHistoryClearResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>9</PAPIErrorCode>

<ErrorMessage/>

</PatronReadingHistoryClearResult>

### Return - Failed

|
| HTTP/1.1 200 OK

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0