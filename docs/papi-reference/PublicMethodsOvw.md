# PAPI Public Methods

_Source: https://documentation.iii.com/polaris/PAPI/current/PAPIService/PublicMethodsOvw.htm_

You are here:

# PAPI Public Methods

The PAPI service supports public methods. These methods fall into one of the following categories:

-

Functions that are basic to building a public facing application. Examples include methods like **BibGet**, **BibHoldingsGet** and **CollectionsGet**. These methods allow users to search bibliographic records and retrieve lists of basic objects in the system. These methods require only basic PAPI authorization.

-

Functions that are specific to a patron's account. Examples include methods like **ItemRenew**, **PatronAccountGet** and **PatronRegistrationUpdate**. These methods allow for features that are in the *My Account* section of an application. You can identify these methods by the **/public/{PatronBarcode}/** route segment. These methods require PAPI authorization with the **AccessSecret** (or the patron's password).

## Using **AccessSecret**

Patron-specific methods must authenticate over a secure connection with the PAPI service using the **AuthenticatePatron** method. When you use this method, PAPI exchanges and verifies the patron’s barcode and password only once. If authentication is successful, you receive an **AccessSecret**, which you can use for the remainder of your operations. For a more secure transaction, use the **AccessSecret** in place of the patron’s password when building the hash for patron methods.

For more authorization information, see PAPI Web Service Authorization.

© 2025 Innovative (Part of Clarivate)
Polaris Version 8.0