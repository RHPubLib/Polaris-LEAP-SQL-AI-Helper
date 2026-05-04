# PatronRegistrationCreate Version 2

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronRegistrationCreate_v2.htm_

You are here:

## PatronRegistrationCreate Version 2

Create a new patron registration record. Basic patron duplicate detection (name, username, barcode) is performed. If "PSPARMDUPDETLEGALPAC" (Patron > Name on ID > PAC) is configured in Polaris System Administration Parameters, then Polaris also compares Name on ID for duplicate detection. If there is a possible duplicate in the database, the following error appears: "Duplicate patron name on identification is specified."

You can allow patrons to self-register and generate a barcode, even if a matching record exists. Go to Polaris Administration (staff client), and select Profiles > PAC > Patron Access Options, the Self-registration tab. Disable duplicate detection.

**Note:** Incoming phone number formats are validated against customer-defined rules in Polaris System Administration.

|
|  
| POST
| /public/1 v2/{LangID}/{AppID}/{OrgID}/patron
|  

### Authorization required?

Yes

### Request Body XML

|
|

<PatronRegistrationDataV2>

<LogonBranchID/>

<LogonUserID/>

<LogonWorkstationID/>

<ReadingListFlag/>

<EmailFormat/>

<DeliveryOptionID/>

<EmailAddress/>

<PhoneVoice1/>

<Password/>

</PatronRegistrationDataV2>

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

Barcode

|

Patron barcode (can be input also if known ahead of time)

|
|

PatronID

|

Polaris patron ID for newly created patron

|
| StatisticalClassID
| Statistical classes are defined by the library as a way of collecting statistics according to whatever categories they'd like to track. Quite often they're used for geographic areas like counties, towns, or school districts.

### XML Body Elements

|
|

Name

|

Required

|

Description/Notes

|
|

LogonBranchID

|

Yes

|

Current branch (can default to System [1])

|
|

LogonUserID

|

Yes

|

Current user (can default to PolarisExec)

|
|

LogonWorkstationID

|

Yes

|

Current workstation (can default to OPACDefault)

|
|

ReadingListFlag

|

No

|

Enable or disable reading list

|
|

EmailFormat

|

No

|

Format of email:

1 - Plain text
2 - HTML

|
|

DeliveryOptionID

|

No

|

Delivery options:

0 - None
1 - Mailing address
2 - Email address
3 - Telephone 1
4 - Telephone 2
5 - Telephone 3
6 - FAX
7 - EDI
8 - TXT messaging

|
|

EmailAddress

|

No

|

Email address

|
|

AltEmailAddress

|

No

|

Alternate email address

|
|

EnableSMS

|

 

|

Enable additional text messages

0 or False - Do not send additional text notice
1 or True - Send additional text notice

|
| PhoneVoice1
| No
| Primary phone number

|
|

PhoneVoice2

|

No

|

Telephone 2 number

|
|

PhoneVoice3

|

No

|

Telephone 3 number

|
|

Phone1CarrierID

|

No

|

Mobile carrier for Telephone 1

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

Sample list from SA_Mobilephonecarriers table:

1 - AT&T
2 - Bell Canada
8 - Sprint
9 - T_Mobile
10 - Tracfone
11 - Verizon
17 - Boost Mobile
22 - Rogers Canada

|
|

Phone2CarrierID

|

No

|

Mobile carrier for Telephone 2

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

|
|

Phone3CarrierID

|

No

|

Mobile carrier for Telephone 3

A value of -2 indicates the carrier is unspecified.

**Note:** The -2 value is supported if the patron's branch has "Notice: Export text message" enabled in System Administration.

|
|

TxtPhoneNumber

|

No

|

Mobile number for text messaging:

1 - PhoneVoice1
2 - PhoneVoice2
3 - PhoneVoice3

Unspecified - Indicates no phone number is specified

|
|

EReceiptOptionID

|

No

|

0 - None
2 - Email receipt
8 - Text message receipt

|
|

Password

| No
|

Patron’s password

|
|

Password2

|

No

|

Patron password duplicate (for verification)

|
| PatronCode
| No
| Patron code assigned to patron

|
| ExpirationDate
| No
| Patron card expiration date

|
| AddrCheckDate
| No
| Patron's address check date

|
| ExcludeFromAlmostOverdueAutoRenew
| No
| Exclude patron from almost overdue/auto-renew reminder notices

|
| ExcludeFromPatronRecExpiration
| No
| Exclude patron from patron record expiration reminder notices

|
| ExcludeFromInactivePatron
| No
| Exclude from inactive patron reminder notices

|
| RequestPickupBranchID
| No
| Branch ID of the patron's preferred pickup location for holds

|
| User1
| No
| User-defined field

|
| User2
| No
| User-defined field

|
| User3
| No
| User-defined field

|
| User4
| No
| User-defined field

|
| User5
| No
| User-defined field

|
| LanguageID
| No
| Patron's language preference

|
| FormerID
| No
| Patron's former barcode

|
| NameFirst
| No
| Patron's first name

|
| NameLast
| No
| Patron's last name

|
| NameMiddle
| No
| Patron's middle name

|
| LegalNameFirst
| No
| Patron's legal first name

|
| LegalNameLast
| No
| Patron's legal last name

|
| LegalNameMiddle
| No
| Patron's legal middle name

|
| UseLegalNameOnNotices
| No
| Use patron's legal name on any notices

|
| Birthdate
| No
| Patron's birth date

|
| GenderID
| No
| Patron's selected gender ID

|
| UserName
| No
| Patron's username

|
| Barcode
| No
| Patron's barcode

|
| PatronBranchID
| No
| Patron's Registered branch ID

|
| StatisticalClassID
| No
| Patron's statistical class code ID

|
| UseSingleName
| No
|

Indicates whether only last name is used on library print and phone notices:

true - Single name used
false - Single name not used

|
| Addresses
| No
| List of addresses for the patron.

#### Addresses Element Sub-Fields

|
|

FreeTextLabel

| No
| Address type label (for example, Home or School) of requested patron address change

|
|

StreetOne

| No
| Patron street one

|
| StreetTwo
| No
| Patron street two

|
| StreetThree
| No
| Patron street three

|
| City
| No
| City of patron address change

|
|

State

| No
|

State of requested patron address change

**Note:** If a *State* field is not required for your country, it can be left unidentified. This requires "StateRequired" to be set to *no* in the System Administration "Countries" table.

|
|

County

| No
| County of requested patron address change

|
|

PostalCode

| No
| Postal code of requested patron address change

|
| ZipPlusFour
| No
| Four digit code added to end of zip code

|
|

Country

| No
| Country of the requested patron address change

|
| CountryID
| No
| Country ID of the requested patron address change

|
|

AddressTypeID

| No
|

Address type of requested patron address change:

1 - Generic
2 - Notices

### Example

|
| http://localhost/PAPIService/REST/public/v2/1033/100/1/patron

### Body

|
|

<PatronRegistrationCreateDataV2>

<LogonBranchID>1</LogonBranchID>

<LogonUserID>1</LogonUserID>

<LogonWorkstationID>1</LogonWorkstationID>

<PatronBranchID>74</PatronBranchID>

<PostalCode>13090</PostalCode>

<City>Liverpool</City>

<State>NY</State>

<StreetOne>100 Main Street</StreetOne>

<NameFirst>John</NameFirst>

<NameLast>Smith</NameLast>

<PhoneVoice1>555-1212</PhoneVoice1>

<EmailAddress>dude@hotmail.com</EmailAddress>

<LanguageID>1</LanguageID>

<UserName>PolarisDude</UserName>

<Password>1234</Password>

<Password2>1234</Password2>

<LegalNameFirst>Johnathan</LegalNameFirst>

<LegalNameLast>Smith</LegalNameLast>

<LegalNameMiddle>Edward</LegalNameMiddle>

<UseLegalNameOnNotices>true</UseLegalNameOnNotices>

<LegalFullName>Johnathan Edward Smith</LegalFullName>

</PatronRegistrationCreateDataV2>

### Return - Success

|
|

HTTP/1.1 200 OK

<PatronRegistrationCreateResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>0</PAPIErrorCode><ErrorMessage/>

<Barcode>PACREG357166</Barcode>

<PatronID>357166</PatronID>

<StatisticalClassID>11</StatisticalClassID>

</PatronRegistrationCreateResult>

### Return - Failed

|
|

<PatronRegistrationCreateResult

xmlns:i="http://www.w3.org/2001/XMLSchemainstance">

<PAPIErrorCode>-1</PAPIErrorCode>

<ErrorMessage>Procedure or function 'PAPI_PatronRegistrationCreate' expects parameter '@nPatronBranchID', which was not supplied.</ErrorMessage>

<Barcode/>

<PatronID>0</PatronID>

<StatisticalClassID>0</StatisticalClassID>

</PatronRegistrationCreateResult>

### Error Messages

|
Code
Description

|
| -200
| Invalid AddressID

|
| -221
| PostalCodes Insert failed

|
| -222
| Invalid PostalCodeLength

|
| -223
| Invalid PostalCodeFormat

|
| -501
| Patron personal information change is not allowed

|
| -3000
| Invalid PatronID specified

|
| -3400
| PatronAddresses insert failed

|
| -3401
| Invalid AddressType

|
| -3500
| Invalid CountryID

|
| -3501
| Invalid PatronBranchID (Not Defined)

|
| -3502
| Invalid PatronBranchID (Not a Branch)

|
| -3505
| Duplicate Barcode

|
| -3515
| Invalid State (Required, but Missing)

|
| -3516
| Invalid City

|
| -3517
| Postal Code not found

|
| -3518
| Invalid Email address

|
| -3519
| Invalid DeliveryMethod Value
(No Address for Patron)

|
| -3520
| Invalid delivery method value (No Email Address for Patron)

|
| -3521
| Invalid DeliveryMethod Value
(No PhoneVoice1 for Patron)

|
| -3522
| Invalid DeliveryMethod Value (No PhoneVoice2 for Patron)

|
| -3523
| Invalid DeliveryMethod Value
(No PhoneVoice3 for Patron)

|
| -3524
| Invalid DeliveryMethod Value
(No PhoneFax for Patron)

|
| -3525
| Invalid DeliveryMethod Value

|
| -3526
| Invalid EmailFormat Value

|
| -3527
| Invalid ReadingList Value

|
| -3529
| Duplicate Username

|
| -3530
| Patron Address Country Not Defined

|
| -3531
| Patron Delivery Notices Address Not Defined

|
| -3532
| Invalid PhoneVoice1

|
| -3533
| Invalid Patron Password Format

|
| -3534
| Invalid Password Length

|
| -3535
| Patron Password Change Is not Allowed

|
| -3536
| Invalid GenderID for the Registered Branch

|
| -3537
| Invalid LegalName Configuration

|
| -3540
| Invalid Birthdate

|
| -3541
| Invalid NameLast Length

|
| -3542
| Invalid NameFirst Length

|
| -3543
| Invalid NameMiddle Length

|
| -3544
| Invalid LegalNameLast Length

|
| -3545
| Invalid LegalNameFirst Length

|
| -3546
| Invalid LegalNameMiddle Length

|
| -3547
| Invalid Username Length

|
| -3548
| Invalid Barcode Length

|
| -3550
| Invalid Patron Barcode

|
| -3551
| Patron Address Not Defined

|
| -3552
| Patron Password Not Defined

|
| -3553
| Patron Address Street One Invalid

|
| -3554
| Patron Address Postal Code Invalid

|
| -3555
| Patron Address City Invalid

|
| -3556
| Patron Address State Invalid

|
| -3612
| Invalid PatronCodeID

|
| -3613
| Invalid PhoneVoice2

|
| -3614
| Invalid PhoneVoice3

|
| -3615
| Invalid Alt Email Address

|
| -3616
| Invalid TXTPhoneNumber

|
| -3617
| Invalid PhoneCarrier

|
| -3618
| Invalid EReceiptOption

|
| -3619
| Invalid DeliveryMethod No Phone

|
| -3620
| Invalid Email Address for EReceipt

|
| -3622
| Invalid RequestPickupBranchID

|
| -3623
| Invalid User1

|
| -3624
| Invalid User2

|
| -3625
| Invalid User3

|
| -3626
| Invalid User4

|
| -3627
| Invalid User5

|
| -3628
| Invalid LanguageID

|
| -3629
| Invalid FormerID

|
| -3630
| Invalid StatisticalClassID for the registered branch

|
| -3634
| Patron required fields missing

|
| -3635
| Invalid Patron Address Country

|
| -3636
| Invalid Patron Address County

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0