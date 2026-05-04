# PatronSavedSearchesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronSavedSearchesGet.htm_

You are here:

## PatronSavedSearchesGet

Returns list of saved searches to the specified patron.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/{PatronBarcode}/savedsearches
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

### XML Elements Returned

One or more searches saved by the patron. The list is sorted in ascending order by last run date.

|
|

Name

|

Description/Notes

|
| PAPIErrorCode
|

Negative values represent errors and are defined elsewhere.

**Note:** On successful completion, the PAPI error code indicates a positive integer representing the number of rows returned.

|
| ErrorMessage
| Error or information message

|
|

SDISearchID

|

Polaris ID of the search record

|
|

SDIName

|

Name of search for identification

|
|

SearchCriteria

|

The search string

|
|

SearchPeriod

|

The search period

|
|

LastRunDate

|

Date the saved search was last run by PolSDIServer

|
|

NotifyOnNoResults

|

Indicates the patron wants notification when a search is run with no results found, contrary is that no email is sent.

|
|

EmailResultsTo

|

The email address to send search results to.

|
|

ResultsCount

|

Number of search results (Bibliographic Records found) for saved searches

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron/21756003332022/
savedsearches

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronSavedSearchesGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>0</PAPIErrorCode>

<ErrorMessage/>

<PatronSavedSearchesGetRows>

<PatronSavedSearchesGetRow>

<SDISearchID>1498</SDISearchID>

<SDIName>Roosevelt</SDIName>

<SearchCriteria>FIND KW={freetext}roosevelt{/freetext} AND AB=3</SearchCriteria>

<SearchPeriod>Monthly</SearchPeriod>

<LastRunDate>2009-02-18T05:11:04</LastRunDate>

<NotifyOnNoResults>true</NotifyOnNoResults>

<EmailResultsTo>dude@polarislibrary.com</EmailResultsTo>

<ResultsCount>10</ResultsCount>

</PatronSavedSearchesGetRow>

...

</PatronSavedSearchesGetRows>

</PatronSavedSearchesGetResult>

### Return - Failed

|
|

HTTP/1.1 200 OK

<PatronSavedSearchesGetResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Specified cast is not valid.</ErrorMessage>

<PatronSavedSearchesGetRows/>

</PatronSavedSearchesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0