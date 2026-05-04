# MultipartGet

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/MultipartGet.htm_

You are here:

## MultipartGet

Returns a list of item barcodes, volumes (nonserial bibliographic items), or designations and volumes (serial issues) when they exist for the specified bibliographic record, patron, and pickup location. Specifying a pickup location is optional.

|
|  
| GET
| /public/1 {Version}/{LangID}/{AppID}/{OrgID}/bib/{BibID}/multiparts/?PatronID={PatronID}
|  

|
|  
| GET
| /public/1/bib/{BibID}/multiparts/?PatronID={PatronID}&PickupLocID={PickupLocID}
|  

### Authorization Required?

Yes, if authentication level set to ALL.

### URI Parameters

|
| Name
|

Required

|

Description/Notes

|
|

BibID

|

Yes

|

The bibliographic record identifier.

|
|

PatronID

|

Yes

|

The patron identifier.

|
| PickupLocID
| No
| Branch ID of the pickup location.

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
| Error or information message.

|
| Type
|

Type of multipart set. Possible values include:

1 - Designation
2 - Volume (multipart set)
3 - Item

|
| Value
| Volume or designation data.

|
| ItemBarcode
| Barcode of the item. Used to place an item-level hold request.

### Examples

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/bib/5000/multiparts?PatronID=2291954

|
|

http://localhost/PAPIService/REST/public/v1/1033/100/1/bib/5000/multiparts?PatronID=2291954&PickupLocID=1001

### Return - Success

|
|

HTTP/1.1 200 OK

<MaterialTypesGetResult xmlns:i="http://www.w3.org/2001/XMLSchema-instance">

<PAPIErrorCode>2</PAPIErrorCode>

<ErrorMessage>

<ErrorMessage />

<MultipartRows>

<MultipartRow>

<Type>1</Type>

<Value>Vol 2 (Feb. 2020)</Value>

</MultipartRow>

<MultipartRow>

<Type>2</Type>

<Value>Vol 1 (Jan. 2020)</Value>

</MultipartRow>

<MultipartRow>

<Type>3</Type>

<Value>Video VOL. 6</Value>

</MultipartRow>

</MultipartRows>

</MaterialTypesGetResult>

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0