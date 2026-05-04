# PatronRegistrationCreate Version 1

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PAPIServicePatronRegistrationCreate_v1.htm_

You are here:

## PatronRegistrationCreate Version 1

Create a new patron registration record. Basic patron duplicate detection (name, username, barcode) is performed. If "PSPARMDUPDETLEGALPAC" (Patron > Name on ID > PAC) is configured in Polaris System Administration Parameters, then Polaris also compares Name on ID for duplicate detection. If there is a possible duplicate in the database, the following error appears: "Duplicate patron name on identification is specified."

You can allow patrons to self-register and generate a barcode, even if a matching record exists. Go to Polaris Administration (staff client), and select Profiles > PAC > Patron Access Options, the Self-registration tab. Disable duplicate detection.

**Note:** Incoming phone number formats are validated against customer-defined rules in Polaris System Administration.

|
|  
| POST
| /public/1 v1/{LangID}/{AppID}/{OrgID}/patron
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
| Name
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

Transaction processing field

|
|

LogonUserID

|

Yes

|

Transaction processing field

|
|

LogonWorkstationID

|

Yes

|

Transaction processing field

|
|

PatronBranchID

|

Yes

|

Patron's registering branch

|
|

PostalCode

|

No

|

Patron postal code

|
|

ZipPlusFour

|

No

|

Four digit code added to end of zip code

|
|

City

|

No

|

Patron city

|
|

State

|

No

|

Patron state

**Note:** If a *State* field is not required for your county, it can be left undefined. This requires StateRequired to be set to *no* in the System Administration Countries table.

|
|

County

|

No

|

Patron county

|
|

CountryID

|

No

|

Patron country

|
|

StreetOne

|

No

|

Patron street one

|
|

StreetTwo

|

No

|

Patron street two

|
| StreetThree
| No
| Patron street three

|
|

NameFirst

|

Yes

|

Patron first name

|
|

NameLast

|

Yes

|

Patron last name

|
|

NameMiddle

|

No

|

Patron middle name

|
|

User1

|

No

|

System-defined field for patron data

|
|

User2

|

No

|

System-defined field for patron data

|
|

User3

|

No

|

System-defined field for patron data

|
|

User4

|

No

|

System-defined field for patron data

|
|

User5

|

No

|

System-defined field for patron data

|
|

Gender

|

No

|

Use M, F, or N (not applicable)

|
|

Birthdate

|

No

|

Patron birth date

|
|

PhoneVoice1

|

No

|

Patron phone

|
|

PhoneVoice2

|

No

|

Patron phone

|
|

PhoneVoice3

|

No

|

Patron phone

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

EmailAddress

|

No

|

Patron email

|
|

AltEmailAddress

|

No

|

Patron alternate email

|
|

LanguageID

|

No

|

Patron languageID - From Languages table

1 - English
2 - Spanish
3 - German
4 - French

|
|

UserName

|

No

|

Online user name

|
|

Password

|

No

|

Patron password

|
|

Password2

|

No

|

Patron password duplicate (for verification)

|
|

DeliveryOptionID

|

No

|

1 - Mail
2 - Email
3 - Telephone 1
4 - Telephone 2
5 - Telephone 3
6 - FAX
7 - EDI
8 - TXT messaging

|
|

EnableSMS

|

No

|

Enable additional text messages:

0 or False - Do not send additional text notice
1 or True - Send additional text notice

|
|

TxtPhoneNumber

|

No

|

Phone number for TXT messaging:

1 - PhoneVoice1
2 - PhoneVoice2
3 - PhoneVoice3

Unspecified - Indicates no phone number is specified

|
|

Barcode

|

No

|

Patron barcode (if not auto-assigning)

|
|

EReceiptOptionID

|

No

|

Ereceipt option ID [4.1 only]:

2 - Email Address
8 - TXT Messaging
100 - All

|
| PatronCode
| No
| ID of patron code assigned to patron. Default used when ID not provided.

|
| ExpirationDate
| No
| Patron card expiration date. Default used when date not provided.

|
| AddrCheckDate
| No
| Patron card address check date. Default used when date not provided.

|
| GenderID
| No
|

Unique code identifying the patron's gender:

1- None (NULL)
2 - Female
3 - Male

If an invalid gender is assigned, PAPI error code -3536 is returned.

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
|

Indicates whether the legal name is used on library print and phone notices:

true - Legal name used
false - Legal name not used

|
| RequestPickupBranchID
| No
| Branch ID of the patron's preferred pickup location for holds

### Example

|
| http://localhost/PAPIService/REST/public/v1/1033/100/1/patron

### Body

|
|

<PatronRegistrationCreateData>

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

</PatronRegistrationCreateData>

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
| PostalCodes insert failed

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
| Invalid State (required, but missing)

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
| Invalid DeliveryMethod value
(No Address for patron)

|
| -3520
| Invalid delivery method value (No Email Address for patron)

|
| -3521
| Invalid DeliveryMethod value
(No PhoneVoice1 for patron)

|
| -3522
| Invalid DeliveryMethod value (No PhoneVoice2 for patron)

|
| -3523
| Invalid DeliveryMethod value
(No PhoneVoice3 for patron)

|
| -3524
| Invalid DeliveryMethod value
(No PhoneFax for patron)

|
| -3525
| Invalid DeliveryMethod value

|
| -3526
| Invalid EmailFormat value

|
| -3527
| Invalid ReadingList value

|
| -3529
| Duplicate Username

|
| -3530
| Patron Address Country not defined

|
| -3531
| Patron Delivery Notices Address not defined

|
| -3532
| Invalid PhoneVoice1

|
| -3533
| Invalid Patron Password format

|
| -3534
| Invalid Password length

|
| -3535
| Patron Password Change is not allowed

|
| -3536
| Invalid GenderID for the registered branch

|
| -3537
| Invalid LegalName configuration

|
| -3540
| Invalid Birthdate

|
| -3541
| Invalid NameLast length

|
| -3542
| Invalid NameFirst length

|
| -3543
| Invalid NameMiddle length

|
| -3544
| Invalid LegalNameLast length

|
| -3545
| Invalid LegalNameFirst length

|
| -3546
| Invalid LegalNameMiddle length

|
| -3547
| Invalid Username length

|
| -3548
| Invalid Barcode length

|
| -3550
| Invalid Patron Barcode

|
| -3551
| Patron Address not defined

|
| -3552
| Patron Password not defined

|
| -3553
| Patron Address Street One invalid

|
| -3554
| Patron Address Postal Code invalid

|
| -3555
| Patron Address City invalid

|
| -3556
| Patron Address State invalid

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

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0