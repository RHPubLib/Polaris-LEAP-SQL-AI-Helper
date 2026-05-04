# PatronLanguagesGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronLanguagesGet.htm_

You are here:

## PatronLanguagesGet

Returns a list of all patron languages in the system.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patron/patronlanguages
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
| LanguageID
| Numeric ID of the language in the system

|
| Description
| English word for the represented language

|
| AdminLanguageID
| Four-number ID of the listed language

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patronlanguages

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronLanguagesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>4</PAPIErrorCode>

<ErrorMessage>

</ErrorMessage>

<PatronLanguagesRows>

<PatronLanguagesRow>

<LanguageID>1</LanguageID>

<Description>English</Description>

<AdminLanguageID>1033</AdminLanguageID>

</PatronLanguagesRow>

<PatronLanguagesRow>

<LanguageID>2</LanguageID>

<Description>Spanish</Description>

<AdminLanguageID>3082</AdminLanguageID>

</PatronLanguagesRow>

<PatronLanguagesRow>

<LanguageID>3</LanguageID>

<Description>German</Description>

<AdminLanguageID>1031</AdminLanguageID>

</PatronLanguagesRow>

<PatronLanguagesRow>

<LanguageID>4</LanguageID>

<Description>French</Description>

<AdminLanguageID>3084</AdminLanguageID>

</PatronLanguagesRow>

</PatronLanguagesRows>

</PatronLanguagesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0