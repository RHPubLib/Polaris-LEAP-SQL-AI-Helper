# SAMobilePhoneCarriersGetResult

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServiceSAMobilePhoneCarriersGetResult.htm_

You are here:

## SAMobilePhoneCarriersGetResult

This method returns content from the SA_MobilePhoneCarriers table for a specified organization, which specifies the mobile phone carrier selections available for patron record phone fields.

|
|  
| GET
| /protected/1 {Version}/{LangID}/{AppID}/{OrgID}/{AccessToken}/sysadmin/mobilephonecarriers
|  

### Authorization required?

Yes

### XML Elements Returned

One or more hold requests placed by the patron. The list is sorted in ascending order by activation date.

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
| CarrierID
| ID of mobile phone carrier

|
| CarrierName
| Name of mobile phone carrier

|
| Email2SMSEmailAddress
| SMS address

|
| NumberOfDigits
| Specifies number of digits in phone number; always 10

|
| Display
| Display flag

### Example

|
| https://qa-saturn.polarislibrary.com/PAPIService/REST/protected/v1/1033/100/3/
OwrTPOlnpRtHYILu4vjKj2cmoGLZQ5zh/sysadmin/mobilephonecarriers

### Return - Success

|
|

HTTP/1.1 200 OK

<SAMobilePhoneCarriersGetResult

xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>26</PAPIErrorCode>

<ErrorMessage></ErrorMessage>

<SAMobilePhoneCarriersGetRows>

<SAMobilePhoneCarriersGetRow>

<CarrierID>1</CarrierID>

<CarrierName>AT&amp;T</CarrierName>

<Email2SMSEmailAddress>@txt.att.net</Email2SMSEmailAddress>

<NumberOfDigits>10</NumberOfDigits>

<Display>true</Display>

</SAMobilePhoneCarriersGetRow>

<SAMobilePhoneCarriersGetRow>

<CarrierID>2</CarrierID>

<CarrierName>Bell Canada</CarrierName>

<Email2SMSEmailAddress>@txt.bellmobility.ca</Email2SMSEmailAddress>

<NumberOfDigits>10</NumberOfDigits>

<Display>false</Display>

</SAMobilePhoneCarriersGetRow>

</SAMobilePhoneCarriersGetRows>

</SAMobilePhoneCarriersGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0