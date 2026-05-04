# PatronTitleListGetTitles

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronTitleListGetTitles.htm_

You are here:

## PatronTitleListGetTitles

Returns all titles, or a range of titles by position in the list, for a specified title list in the patron account.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/patrontitlelistgettitles?list={list_id}&start
Position={StartPosition}&endPosition={EndPosition}
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
| PatronBarcode
| Yes
| Barcode of patron.

|
| list
| Yes
| Record ID of the list

|
| StartPosition
| No
| Position in the list of the first title to return

|
| EndPosition
| No
| Position in the list of the last title to return

**Note: **
If you find that a very large title list is not returned in its entirety, use the **start_position** and **end_position** parameters to have the list returned in smaller "chunks."

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

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
patrontitlelistgettitles?list=3

http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
patrontitlelistgettitles?list=3&startPosition=3&endPosition=8

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronTitleListGetTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronTitleListTitleRows>

<PatronTitleListTitleRow>

<Position>1</Position>

<RecordID>9378</RecordID>

<Name>Quick &amp; Easy Cooking for One [electronic resource]</Name>

<LocalControlNumber>995136</LocalControlNumber>

</PatronTitleListTitleRow>

<PatronTitleListTitleRow>

<Position>2</Position>

<RecordID>9379</RecordID>

<Name>Quick &amp; Easy Cooking for One [electronic resource]</Name>

<LocalControlNumber>995136</LocalControlNumber>

</PatronTitleListTitleRow>

</PatronTitleListTitleRows>

</PatronTitleListGetTitlesResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronTitleListGetTitlesResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Could not retrieve records because record-store '999' does not exist.</ErrorMessage>

<PatronTitleListTitleRows/>

</PatronTitleListGetTitlesResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0