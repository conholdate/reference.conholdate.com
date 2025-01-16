---
title: Skapa ny digital signaturlinje och ställ in leverantörs-ID
linktitle: Skapa ny digital signaturlinje och ställ in leverantörs-ID
second_title: Aspose.Words Document Processing API
description: Upptäck hur du programmatiskt lägger till signaturrader till dina Word-dokument med Aspose.Words för .NET. Den här omfattande guiden täcker allt från att ställa in din utvecklingsmiljö till att infoga signaturrader och signera dokument på ett säkert sätt.
type: docs
weight: 10
url: /sv/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Introduktion

Hej alla teknikentusiaster! Har du någonsin velat automatisera inkluderingen av signaturrader i dina Word-dokument? Idag fördjupar vi oss i hur man uppnår detta med Aspose.Words för .NET. Den här steg-för-steg-guiden leder dig genom att skapa en signaturrad och ställa in leverantörs-ID, vilket gör dina dokumentbearbetningsuppgifter mer effektiva och strömlinjeformade.

## Förutsättningar

Innan vi hoppar in, låt oss se till att du har allt inrättat:

1.  Aspose.Words för .NET: Om du inte har installerat det ännu, ladda ner det[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: Använd Visual Studio eller någon C#-utvecklingsinställning.
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.
4. PFX-certifikat: Du behöver ett PFX-certifikat för att signera dokument, som kan erhållas från en betrodd certifikatutfärdare.

## Importera nödvändiga namnområden

För att komma igång, importera de nödvändiga namnrymden till ditt C#-projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Låt oss nu dyka in i detaljerna för att skapa en ny signaturrad och ställa in leverantörs-ID.

## Steg 1: Skapa ett nytt dokument

Först måste vi skapa ett nytt Word-dokument, som kommer att fungera som arbetsytan för vår signaturrad:

```csharp
// Ange sökvägen till din dokumentkatalog.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Här initierar vi en ny`Document` och a`DocumentBuilder`, vilket gör att vi enkelt kan lägga till element.

## Steg 2: Definiera signaturlinjealternativ

Därefter kommer vi att definiera alternativen för vår signaturrad, inklusive undertecknarens namn, titel, e-post och annan relevant information:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Dessa alternativ hjälper till att anpassa signaturlinjen, vilket gör den tydlig och professionell.

## Steg 3: Sätt in signaturraden

Med våra alternativ redo kan vi nu infoga signaturraden i dokumentet:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 De`InsertSignatureLine` metod lägger till signaturraden och vi tilldelar den ett unikt leverantörs-ID.

## Steg 4: Spara dokumentet

Efter att ha infogat signaturraden, låt oss spara dokumentet:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Detta sparar ditt dokument med den nyligen tillagda signaturraden.

## Steg 5: Ställ in signeringsalternativ

Nu kommer vi att konfigurera signeringsalternativen, inklusive signaturrads-ID, leverantörs-ID, kommentarer och signeringstiden:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Dessa inställningar säkerställer att dokumentet är signerat med korrekta uppgifter.

## Steg 6: Skapa certifikatinnehavare

För att signera dokumentet måste vi skapa en certifikatinnehavare med PFX-certifikatet:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Ersätta`"morzal.pfx"` med ditt faktiska certifikatfilnamn och`"aw"` med ditt certifikatlösenord.

## Steg 7: Signera dokumentet

Slutligen kommer vi att signera dokumentet med hjälp av verktyget för digitala signaturer:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Denna process signerar dokumentet och sparar det som en ny fil.

## Slutsats

Grattis! Du har framgångsrikt skapat en signaturrad och angett leverantörs-ID i ett Word-dokument med Aspose.Words för .NET. Detta kraftfulla bibliotek förenklar dokumentbearbetningsuppgifter, vilket gör ditt arbetsflöde mer effektivt. Ge det ett försök och se hur det kan förbättra dina projekt!

## FAQ's

### Kan jag anpassa utseendet på signaturlinjen?
 Absolut! Du kan justera olika alternativ i`SignatureLineOptions` för att passa din stil och krav.

### Vad händer om jag inte har ett PFX-certifikat?
Du kommer att behöva skaffa ett från en betrodd certifikatutfärdare, eftersom det är viktigt för digital signering av dokument.

### Kan jag lägga till flera signaturrader i ett dokument?
Ja, du kan lägga till flera signaturrader genom att upprepa infogningsprocessen med olika alternativ.

### Är Aspose.Words for .NET kompatibelt med .NET Core?
Ja, Aspose.Words för .NET stöder .NET Core, vilket gör den mångsidig för olika utvecklingsmiljöer.

### Hur säkra är de digitala signaturerna?
Digitala signaturer skapade med Aspose.Words är mycket säkra, förutsatt att du använder ett giltigt och pålitligt certifikat.