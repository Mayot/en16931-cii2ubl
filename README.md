# en16931-cii2ubl

Converter for unidirectional EN16931 invoices from CII D16B to UBL 2.1 and 2.2.

This is a Java 1.8+ library that converts a Cross Industry Invoice (CII) into a Universal Business Language (UBL) document following the rules of the European Norm (EN) 16931 that defines a common semantic data model for electronic invoices in Europe.  

See https://peppol.helger.com/public/locale-en_US/menuitem-tools-rest-api#cii2ubl for a service implementation using this library.

This library is licensed under the Apache License Version 2.0.

# Usage

This is a pure Java library and not a self-contained conversion tool.
You can convert CII D16B invoices following the EN 16931 rules to both UBL 2.1 and UBL 2.2.
The entrance classes are:
* `com.helger.en16931.cii2ubl.CIIToUBL21Converter`
* `com.helger.en16931.cii2ubl.CIIToUBL22Converter`

The main conversion method is called `convertCIItoUBL` and takes either a `File` as input or a pre-parsed `un.unece.uncefact.data.standard.crossindustryinvoice._100.CrossIndustryInvoiceType` object (that reading is done with class `com.helger.cii.d16b.CIID16BReader` from [ph-cii](https://github.com/phax/ph-cii)).
Additionally an `ErrorList` object must be provided as a container for all the errors that occur.


## Maven usage

```xml
<dependency>
  <groupId>com.helger</groupId>
  <artifactId>en16931-cii2ubl</artifactId>
  <version>1.1.5</version>
</dependency>
```

# Open issues

* The migration of CII `NetPriceProductTradePrice/BasisQuantity` to UBL `Price/BaseQuantity` is not consistent for me
    * See example files 2, 8 and 9
    * The UBL example files use a BaseQuanity of 1 in all cases

# News and noteworthy

* v1.1.6 - work in progress
    * Verified against EN 16931 validation artefacts 1.3.0 - no changes in the output
* v1.1.5 - 2019-09-13
    * Added possibility to enforce invoice creation
* v1.1.4 - 2019-07-15
    * Updated to EN 16931 validation artefacts 1.2.3
* v1.1.3 - 2019-05-15
    * Updated to EN 16931 validation artefacts 1.2.1
* v1.1.2 - 2019-04-26
    * Updated to EN 16931 validation artefacts 1.2.0
* v1.1.1 - 2019-02-27
    * Improved delivery date handling
    * Improved price base quantity handling
* v1.1.0 - 2019-02-26
    * Added support to create UBL 2.1 Invoice and CreditNote
* v1.0.0 - 2019-02-26
    * Initial release creating UBL 2.2 Invoice and CreditNote

---

My personal [Coding Styleguide](https://github.com/phax/meta/blob/master/CodingStyleguide.md) |
On Twitter: <a href="https://twitter.com/philiphelger">@philiphelger</a> |
Kindly supported by [YourKit Java Profiler](https://www.yourkit.com)