---
title: Lägga till anpassade dokumentegenskaper i Word
linktitle: Lägga till anpassade dokumentegenskaper i Word
second_title: Aspose.Words Document Processing API
description: Lär dig hur du förbättrar dina Word-dokument med anpassade dokumentegenskaper med Aspose.Words för .NET. Denna omfattande guide leder dig genom processen.
type: docs
weight: 10
url: /sv/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Introduktion

Välkomna! Om du utforskar Aspose.Words för .NET och vill lära dig hur du lägger till anpassade dokumentegenskaper till dina Word-filer, är du på rätt plats. Anpassade egenskaper är ovärderliga för att lagra ytterligare metadata som inbyggda egenskaper inte täcker. Oavsett om du behöver spåra dokumentauktorisering, revisionsnummer eller specifika datum, kan anpassade egenskaper hjälpa. I den här handledningen guidar vi dig genom stegen för att lägga till dessa egenskaper sömlöst med Aspose.Words för .NET. Låt oss komma igång!

## Förutsättningar

Innan du dyker in i koden, se till att du har följande:

1.  Aspose.Words för .NET Library: Ladda ner det[här](https://releases.aspose.com/words/net/).
2. Utvecklingsmiljö: En IDE som Visual Studio.
3. Grundläggande kunskaper i C#: Bekantskap med C# och .NET kommer att vara till hjälp.
4.  Exempeldokument: Förbered ett exempel på Word-dokument med namnet`Properties.docx` för modifiering.

## Importera namnområden

För att komma åt funktionerna i Aspose.Words måste du importera de nödvändiga namnrymden i början av din kod:

```csharp
using System;
using Aspose.Words;
```

## Steg 1: Konfigurera dokumentsökvägen

 Låt oss sedan definiera sökvägen till ditt Word-dokument. Detta steg är viktigt för att hitta och öppna din`Properties.docx` fil.

```csharp
// Ange sökvägen till din dokumentkatalog.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Se till att byta ut`"YOUR DOCUMENT DIRECTORY"` med den faktiska sökvägen till ditt dokument.

## Steg 2: Åtkomst till anpassade dokumentegenskaper

Låt oss nu komma åt de anpassade dokumentegenskaperna för Word-dokumentet, där dina anpassade metadata kommer att finnas.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Den här raden ger dig tillgång till samlingen av anpassade egenskaper som du kommer att arbeta med.

## Steg 3: Kontrollera efter befintliga egenskaper

Innan du lägger till nya egenskaper är det klokt att kontrollera om en fastighet redan finns för att undvika dubbelarbete.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Den här koden kontrollerar om egenskapen "Authorized" redan finns. Om den gör det, avslutas metoden tidigt, vilket förhindrar dubbletter.

## Steg 4: Lägga till en boolesk egenskap

Låt oss lägga till en anpassad boolesk egenskap för att indikera om dokumentet är auktoriserat.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Den här raden lägger till en egenskap som heter "Authorized" och anger dess värde till`true`.

## Steg 5: Lägga till en strängegenskap

Därefter anger vi vem som auktoriserade dokumentet genom att lägga till en strängegenskap.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Byt gärna ut "John Smith" med vilket namn du föredrar.

## Steg 6: Lägga till en datumegenskap

För att spåra när dokumentet auktoriserades, låt oss lägga till en datumegenskap.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Den här raden lägger till en egenskap som heter "Authorized Date" och tilldelar den dagens datum med hjälp av`DateTime.Today`.

## Steg 7: Lägga till ett revisionsnummer

För versionskontroll kan vi lägga till en egenskap för att hålla reda på dokumentets versionsnummer.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Här lägger vi till en "Authorized Revision"-egenskap som innehåller dokumentets aktuella revisionsnummer.

## Steg 8: Lägga till en numerisk egenskap

Låt oss slutligen lägga till en numerisk egenskap för att lagra ett auktoriserat belopp, till exempel en budgetsiffra.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Den här raden lägger till en egenskap som heter "Authorized Amount" med värdet på`123.45`. Du kan justera detta nummer efter behov.

## Slutsats

Grattis! Du har framgångsrikt lagt till anpassade dokumentegenskaper till ett Word-dokument med Aspose.Words för .NET. Dessa egenskaper är ett kraftfullt sätt att lagra metadata som är skräddarsydda efter dina krav, oavsett om det gäller spårning av auktoriseringsdetaljer, revisionsnummer eller specifika belopp.

## FAQ's

### Vad är anpassade dokumentegenskaper?
Anpassade dokumentegenskaper är metadata som du kan lägga till i ett Word-dokument för att lagra ytterligare information som inte täcks av inbyggda egenskaper.

### Kan jag lägga till andra egenskaper än strängar och siffror?
Ja, du kan lägga till olika typer av egenskaper, inklusive booleska värden, datum och till och med anpassade objekt.

### Hur kommer jag åt dessa egenskaper i ett Word-dokument?
Du kan komma åt anpassade egenskaper programmatiskt med Aspose.Words eller visa dem direkt i Word genom dokumentegenskaperna.

### Är det möjligt att redigera eller ta bort anpassade egenskaper?
Absolut! Du kan enkelt redigera eller ta bort anpassade egenskaper med metoder som tillhandahålls av Aspose.Words.

### Kan anpassade egenskaper användas för att filtrera dokument?
Ja! Anpassade egenskaper är utmärkta för att kategorisera och filtrera dokument baserat på specifik metadata.