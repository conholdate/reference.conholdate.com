---
title: Skapa och signera ny signaturlinje
linktitle: Skapa och signera ny signaturlinje
second_title: Aspose.Words Document Processing API
description: Lär dig hur du sömlöst lägger till en digital signatur till dina Word-dokument med Aspose.Words för .NET. Den här omfattande handledningen täcker allt från att ställa in din miljö och infoga en signaturrad till att spara och verifiera dina signerade dokument.
type: docs
weight: 10
url: /sv/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Introduktion

Vill du lägga till en digital signatur i ett Word-dokument? Med Aspose.Words för .NET är det enklare än du kanske tror! Denna handledning guidar dig genom stegen för att ställa in din miljö, lägga till en signaturrad och signera ditt dokument digitalt. Låt oss komma igång!

## Förutsättningar

Innan du dyker in i koden, se till att du har följande:

1.  Aspose.Words för .NET -[Ladda ner den här](https://releases.aspose.com/words/net/).
2. .NET-utvecklingsmiljö - Visual Studio är idealisk för denna uppgift.
3. Dokument att signera - Du kan skapa ett nytt Word-dokument eller använda ett befintligt.
4.  Certifikatfil - A`.pfx` filen är nödvändig för digitala signaturer.
5. Signaturlinjebild (valfritt) - Du kan inkludera en bildfil för signaturen.

## Importera nödvändiga namnområden

För att använda funktionerna i Aspose.Words måste du importera följande namnrymder:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Steg 1: Konfigurera dokumentkatalogen

Börja med att definiera sökvägen till din dokumentkatalog. Det är här du sparar och hämtar dina dokument.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Ange sökvägen till din dokumentkatalog
```

## Steg 2: Skapa ett nytt dokument

Låt oss sedan skapa ett nytt Word-dokument. Detta dokument kommer att fungera som arbetsytan för din signaturlinje.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Steg 3: Infoga signaturlinjen

 Använd nu`DocumentBuilder` klass för att infoga en signaturrad i ditt dokument:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Steg 4: Spara dokumentet

När du har infogat signaturraden sparar du dokumentet. Detta är ett avgörande steg innan du skriver under.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Steg 5: Konfigurera signeringsalternativ

Ställ in alternativen för signeringsprocessen. Detta inkluderar att specificera signaturrads-ID och den valfria bilden som ska visas med signaturen.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Vägen till din bild
};
```

## Steg 6: Laddar certifikatet

Ladda certifikatfilen som krävs för att signera dokumentet:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Justera filnamn och lösenord
```

## Steg 7: Signera dokumentet

 Slutligen, underteckna dokumentet med hjälp av`DigitalSignatureUtil` klass. Spara det undertecknade dokumentet med ett nytt namn för framtida referens.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Slutsats

Grattis! Du har framgångsrikt skapat ett Word-dokument, lagt till en signaturrad och signerat det digitalt med Aspose.Words för .NET. Detta kraftfulla verktyg förenklar dokumentautomatisering och säkerställer att dina kontrakt och formella dokument är säkert signerade och autentiserade.

## FAQ's

### Kan jag använda andra bildformat för signaturraden?

Ja, du kan använda olika bildformat, inklusive PNG, JPG och BMP.

###  Är det nödvändigt att använda en`.pfx` file for the certificate?

 Ja, a`.pfx` fil är ett standardformat för att lagra certifikat och privata nycklar för digitala signaturer.

### Kan jag lägga till flera signaturrader i ett enda dokument?

Absolut! Du kan infoga flera signaturrader genom att upprepa infogningssteget efter behov.

### Vad händer om jag inte har ett digitalt certifikat?

Du måste skaffa ett digitalt certifikat från en betrodd certifikatutfärdare eller skapa ett med hjälp av verktyg som OpenSSL.

### Hur verifierar jag den digitala signaturen i dokumentet?

Du kan verifiera den digitala signaturen genom att öppna det signerade dokumentet i Word och kontrollera signaturdetaljerna för att bekräfta dess äkthet och integritet.