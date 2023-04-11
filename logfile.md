# Complete log file after reading a Credit Card

## Log file for a MasterCard
```plaintext
NFC tag discovered
TagId: 028eedb17074b0
TechList found with these entries:
android.nfc.tech.IsoDep
android.nfc.tech.NfcA
connection with card success

*********************************
************ step 00 ************
* our journey begins            *
*********************************
increase IsoDep timeout for long lasting reading
timeout old: 2000 ms
timeout new: 10000 ms

*********************************
************ step 01 ************
* select PPSE                   *
*********************************
01 select PPSE command  length 20 data: 00a404000e325041592e5359532e444446303100
01 select PPSE response length 64 data: 6f3c840e325041592e5359532e4444463031a52abf0c2761254f07a000000004101050104465626974204d6173746572436172648701019f0a04000101019000
------------------------------------
6F 3C -- File Control Information (FCI) Template
      84 0E -- Dedicated File (DF) Name
            32 50 41 59 2E 53 59 53 2E 44 44 46 30 31 (BINARY)
      A5 2A -- File Control Information (FCI) Proprietary Template
            BF 0C 27 -- File Control Information (FCI) Issuer Discretionary Data
                     61 25 -- Application Template
                           4F 07 -- Application Identifier (AID) - card
                                 A0 00 00 00 04 10 10 (BINARY)
                           50 10 -- Application Label
                                 44 65 62 69 74 20 4D 61 73 74 65 72 43 61 72 64 (=Debit MasterCard)
                           87 01 -- Application Priority Indicator
                                 01 (BINARY)
                           9F 0A 04 -- [UNKNOWN TAG]
                                    00 01 01 01 (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------


*********************************
************ step 02 ************
* search applications on card   *
*********************************
02 analyze select PPSE response and search for tag 0x4F (applications on card)
Found tag 0x4F 1 time:
application Id (AID): a0000000041010


*********************************
************ step 03 ************
* select application by AID     *
*********************************
03 select application by AID a0000000041010 (number 1)

03 select AID command  length 13 data: 00a4040007a000000004101000
03 select AID response length 86 data: 6f528407a0000000041010a54750104465626974204d6173746572436172649f12104465626974204d6173746572436172648701019f1101015f2d046465656ebf0c119f0a04000101019f6e07028000003030009000
------------------------------------
6F 52 -- File Control Information (FCI) Template
      84 07 -- Dedicated File (DF) Name
            A0 00 00 00 04 10 10 (BINARY)
      A5 47 -- File Control Information (FCI) Proprietary Template
            50 10 -- Application Label
                  44 65 62 69 74 20 4D 61 73 74 65 72 43 61 72 64 (=Debit MasterCard)
            9F 12 10 -- Application Preferred Name
                     44 65 62 69 74 20 4D 61 73 74 65 72 43 61 72 64 (=Debit MasterCard)
            87 01 -- Application Priority Indicator
                  01 (BINARY)
            9F 11 01 -- Issuer Code Table Index
                     01 (NUMERIC)
            5F 2D 04 -- Language Preference
                     64 65 65 6E (=deen)
            BF 0C 11 -- File Control Information (FCI) Issuer Discretionary Data
                     9F 0A 04 -- [UNKNOWN TAG]
                              00 01 01 01 (BINARY)
                     9F 6E 07 -- Visa Low-Value Payment (VLP) Issuer Authorisation Code
                              02 80 00 00 30 30 00 (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------


*********************************
************ step 04 ************
* search for tag 0x9F38         *
*********************************
04 search for tag 0x9F38 in the selectAid response
Available predefined values for PDOL and CDOL
List of predefined tag and values for PDOL and CDOL
Tag  Name                            Value
-------------------------------------------------
9f66 Terminal Transaction Qualifiers 27000000
9f66 Terminal Transaction Qualifiers 27000000
9f66 Terminal Transaction Qualifiers b7604000
9f66 Terminal Transaction Qualifiers a0000000
9f66 Terminal Transaction Qualifiers f0204000
9f02 Transaction Amount              000000001000
9f03 Amount, Other (Numeric)         000000000000
9f1a Terminal Country Code           0978
95   Terminal Verificat.Results      0000000000
5f2a Transaction Currency Code       0978
9a   Transaction Date                230301
9c   Transaction Type                00
9f37 Unpredictable Number            38393031
9f35 Terminal Type                   22
9f45 Data Authentication Code        0000
9f4c ICC Dynamic Number              0000000000000000
9f34 Terminal Transaction Qualifiers 000000
9f21 Transaction Time (HHMMSS)       111009
9f7c Merchant Custom Data            0000000000000000000000000000
00   Tag not found                   00


### processing the MasterCard path ###

No PDOL found in the selectAid response, generating a 'null' PDOL

The card is requesting 0 tags in the PDOL

Tag  Tag Name                        Length Value
-----------------------------------------------------
     no PDOL provided, returning an empty command
-----------------------------------------------------

*********************************
************ step 05 ************
* get the processing options    *
*********************************
05 get the processing options  command length: 8 data: 80a8000002830000
05 get the processing options response length: 22 data: 771282021980940c0801010010010101200102009000
------------------------------------
77 12 -- Response Message Template Format 2
      82 02 -- Application Interchange Profile
            19 80 (BINARY)
      94 0C -- Application File Locator (AFL)
            08 01 01 00 10 01 01 01 20 01 02 00 (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------

*********************************
************ step 99 ************
* our journey ends              *
*********************************
```

## Log file for a VisaCard
```plaintext
NFC tag discovered
TagId: 0585921afb9100
TechList found with these entries:
android.nfc.tech.IsoDep
android.nfc.tech.NfcA
connection with card success

*********************************
************ step 00 ************
* our journey begins            *
*********************************
increase IsoDep timeout for long lasting reading
timeout old: 2000 ms
timeout new: 10000 ms

*********************************
************ step 01 ************
* select PPSE                   *
*********************************
01 select PPSE command  length 20 data: 00a404000e325041592e5359532e444446303100
01 select PPSE response length 62 data: 6f3a840e325041592e5359532e4444463031a528bf0c2561234f07a0000000031010500a566973612044656269748701019f0a0800010501000000009000
------------------------------------
6F 3A -- File Control Information (FCI) Template
      84 0E -- Dedicated File (DF) Name
            32 50 41 59 2E 53 59 53 2E 44 44 46 30 31 (BINARY)
      A5 28 -- File Control Information (FCI) Proprietary Template
            BF 0C 25 -- File Control Information (FCI) Issuer Discretionary Data
                     61 23 -- Application Template
                           4F 07 -- Application Identifier (AID) - card
                                 A0 00 00 00 03 10 10 (BINARY)
                           50 0A -- Application Label
                                 56 69 73 61 20 44 65 62 69 74 (=Visa Debit)
                           87 01 -- Application Priority Indicator
                                 01 (BINARY)
                           9F 0A 08 -- [UNKNOWN TAG]
                                    00 01 05 01 00 00 00 00 (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------


*********************************
************ step 02 ************
* search applications on card   *
*********************************
02 analyze select PPSE response and search for tag 0x4F (applications on card)
Found tag 0x4F 1 time:
application Id (AID): a0000000031010


*********************************
************ step 03 ************
* select application by AID     *
*********************************
03 select application by AID a0000000031010 (number 1)

03 select AID command  length 13 data: 00a4040007a000000003101000
03 select AID response length 115 data: 6f6f8407a0000000031010a564500a566973612044656269749f120f636f6d6469726563742044656269749f1101018701015f2d046465656e9f38189f66049f02069f03069f1a0295055f2a029a039c019f3704bf0c1a9f0a0800010501000000009f5a053109780276bf6304df2001809000
------------------------------------
6F 6F -- File Control Information (FCI) Template
      84 07 -- Dedicated File (DF) Name
            A0 00 00 00 03 10 10 (BINARY)
      A5 64 -- File Control Information (FCI) Proprietary Template
            50 0A -- Application Label
                  56 69 73 61 20 44 65 62 69 74 (=Visa Debit)
            9F 12 0F -- Application Preferred Name
                     63 6F 6D 64 69 72 65 63 74 20 44 65 62 69 74 (=comdirect Debit)
            9F 11 01 -- Issuer Code Table Index
                     01 (NUMERIC)
            87 01 -- Application Priority Indicator
                  01 (BINARY)
            5F 2D 04 -- Language Preference
                     64 65 65 6E (=deen)
            9F 38 18 -- Processing Options Data Object List (PDOL)
                     9F 66 04 -- Terminal Transaction Qualifiers
                     9F 02 06 -- Amount, Authorised (Numeric)
                     9F 03 06 -- Amount, Other (Numeric)
                     9F 1A 02 -- Terminal Country Code
                     95 05 -- Terminal Verification Results (TVR)
                     5F 2A 02 -- Transaction Currency Code
                     9A 03 -- Transaction Date
                     9C 01 -- Transaction Type
                     9F 37 04 -- Unpredictable Number
            BF 0C 1A -- File Control Information (FCI) Issuer Discretionary Data
                     9F 0A 08 -- [UNKNOWN TAG]
                              00 01 05 01 00 00 00 00 (BINARY)
                     9F 5A 05 -- Terminal transaction Type (Interac)
                              31 09 78 02 76 (BINARY)
                     BF 63 04 -- [UNKNOWN TAG]
                              DF 20 01 -- [UNKNOWN TAG]
                                       80 (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------


*********************************
************ step 04 ************
* search for tag 0x9F38         *
*********************************
04 search for tag 0x9F38 in the selectAid response
Available predefined values for PDOL and CDOL
List of predefined tag and values for PDOL and CDOL
Tag  Name                            Value
-------------------------------------------------
9f66 Terminal Transaction Qualifiers 27000000
9f66 Terminal Transaction Qualifiers 27000000
9f66 Terminal Transaction Qualifiers b7604000
9f66 Terminal Transaction Qualifiers a0000000
9f66 Terminal Transaction Qualifiers f0204000
9f02 Transaction Amount              000000001000
9f03 Amount, Other (Numeric)         000000000000
9f1a Terminal Country Code           0978
95   Terminal Verificat.Results      0000000000
5f2a Transaction Currency Code       0978
9a   Transaction Date                230301
9c   Transaction Type                00
9f37 Unpredictable Number            38393031
9f35 Terminal Type                   22
9f45 Data Authentication Code        0000
9f4c ICC Dynamic Number              0000000000000000
9f34 Terminal Transaction Qualifiers 000000
9f21 Transaction Time (HHMMSS)       111009
9f7c Merchant Custom Data            0000000000000000000000000000
00   Tag not found                   00


### processing the American Express, VisaCard and GiroCard path ###

found tag 0x9F38 (PDOL) in the selectAid with this length: 24 data: 9f66049f02069f03069f1a0295055f2a029a039c019f3704

The card is requesting 9 tags in the PDOL

Tag  Tag Name                        Length Value
-----------------------------------------------------
9f66 Terminal Transaction Qualifiers     4  27 00 00 00 
9f02 Amount, Authorised (Numeric)        6  00 00 00 00 10 00 
9f03 Amount, Other (Numeric)             6  00 00 00 00 00 00 
9f1a Terminal Country Code               2  09 78 
95   Terminal Verification Results (TVR) 5  00 00 00 00 00 
5f2a Transaction Currency Code           2  09 78 
9a   Transaction Date                    3  23 03 01 
9c   Transaction Type                    1  00 
9f37 Unpredictable Number                4  38 39 30 31 
-----------------------------------------------------


*********************************
************ step 05 ************
* get the processing options    *
*********************************
05 get the processing options  command length: 41 data: 80a8000023832127000000000000001000000000000000097800000000000978230301003839303100
05 get the processing options response length: 203 data: 7781c68202202094041001030057134871780082770574d25072211328662101000f9f100706011203a000009f2608c428942a8511a9879f2701809f360200e59f6c0204009f4b818031919d3560b1329ad30a5778a6ef207e90ee785a461a30d411b577e16dfca10516302b29cf85b3754a7cc25b8decc126cac7475dca96482fbc774161dcf0deb25a9603e2e2e333a341fd2fb02f495f485682d11baa4361d4b989f9970f374c7ac351aba5402ca202d8c105777204e60ff3c71d89171c1ceb49a2fd884a2f260c9000
------------------------------------
77 81 C6 -- Response Message Template Format 2
         82 02 -- Application Interchange Profile
               20 20 (BINARY)
         94 04 -- Application File Locator (AFL)
               10 01 03 00 (BINARY)
         57 13 -- Track 2 Equivalent Data
               48 71 78 00 82 77 05 74 D2 50 72 21 13 28 66 21
               01 00 0F (BINARY)
         9F 10 07 -- Issuer Application Data
                  06 01 12 03 A0 00 00 (BINARY)
         9F 26 08 -- Application Cryptogram
                  C4 28 94 2A 85 11 A9 87 (BINARY)
         9F 27 01 -- Cryptogram Information Data
                  80 (BINARY)
         9F 36 02 -- Application Transaction Counter (ATC)
                  00 E5 (BINARY)
         9F 6C 02 -- Mag Stripe Application Version Number (Card)
                  04 00 (BINARY)
         9F 4B 81 80 -- Signed Dynamic Application Data
                     31 91 9D 35 60 B1 32 9A D3 0A 57 78 A6 EF 20 7E
                     90 EE 78 5A 46 1A 30 D4 11 B5 77 E1 6D FC A1 05
                     16 30 2B 29 CF 85 B3 75 4A 7C C2 5B 8D EC C1 26
                     CA C7 47 5D CA 96 48 2F BC 77 41 61 DC F0 DE B2
                     5A 96 03 E2 E2 E3 33 A3 41 FD 2F B0 2F 49 5F 48
                     56 82 D1 1B AA 43 61 D4 B9 89 F9 97 0F 37 4C 7A
                     C3 51 AB A5 40 2C A2 02 D8 C1 05 77 72 04 E6 0F
                     F3 C7 1D 89 17 1C 1C EB 49 A2 FD 88 4A 2F 26 0C (BINARY)
90 00 -- Command successfully executed (OK)
------------------------------------


*********************************
************ step 99 ************
* our journey ends              *
*********************************
```