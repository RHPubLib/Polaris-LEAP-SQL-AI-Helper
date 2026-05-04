# PatronUdfConfigsGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PatronUdfConfigsGet.htm_

You are here:

## PatronUdfConfigsGet

Returns the possible user-defined values, when user-defined fields are not configured as free-text. This endpoint also includes information about the system administration configuration of the user-defined fields, including which fields are configured for display and which fields are required.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/patronudfs
|  

### Authorization Required

Yes, if authentication level set to ALL.

### Public Method

Yes

### XML elements returned

The following table lists item status elements returned.

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

http://localhost/PAPIService/REST/public/v1/1033/100/235/patronudfs

### Result - Success

|
|

HTTP/1.1 200 OK

<PatronUdfConfigsGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>5</PAPIErrorCode>

<ErrorMessage i:nil="true" />

<PatronUdfConfigsRows>

<PatronUdfConfigsRow>

<PatronUdfID>1</PatronUdfID>

<Label>ID Number</Label>

<Display>false</Display>

<Values>999999</Values>

<Required>false</Required>

<DefaultValue>999999</DefaultValue>

</PatronUdfConfigsRow>

<PatronUdfConfigsRow>

<PatronUdfID>2</PatronUdfID>

<Label>Privileges / Restrictions</Label>

<Display>true</Display>

<Values></Values>

<Required>true</Required>

<DefaultValue></DefaultValue>

</PatronUdfConfigsRow>

<PatronUdfConfigsRow>

<PatronUdfID>3</PatronUdfID>

<Label>Voter Registration</Label>

<Display>true</Display>

<Values></Values>

<Required>false</Required>

<DefaultValue></DefaultValue>

</PatronUdfConfigsRow>

<PatronUdfConfigsRow>

<PatronUdfID>4</PatronUdfID>

<Label>Library Newsletter</Label>

<Display>true</Display>

<Values>Yes,No</Values>

<Required>true</Required>

<DefaultValue>No</DefaultValue>

</PatronUdfConfigsRow>

<PatronUdfConfigsRow>

<PatronUdfID>5</PatronUdfID>

<Label>Favorite Brady</Label>

<Display>false</Display>

<Values>Mike,Marcia,Sam the Butcher</Values>

<Required>false</Required>

<DefaultValue></DefaultValue>

</PatronUdfConfigsRow>

</PatronUdfConfigsRows>

</PatronUdfConfigsGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0