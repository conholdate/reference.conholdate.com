---
title: Tekst toevoegen uit gemarkeerde secties in Word-documenten
linktitle: Tekst toevoegen uit gemarkeerde secties in Word-documenten
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u naadloos tekst uit gemarkeerde secties van een Word-document kunt toevoegen met Aspose.Words voor .NET. Deze stapsgewijze tutorial.
type: docs
weight: 10
url: /nl/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Invoering

Heb je het ooit lastig gevonden om tekst toe te voegen uit een bladwijzersectie in een Word-document? Dan ben je hier aan het juiste adres! Deze tutorial leidt je stap voor stap door het proces met Aspose.Words voor .NET. Aan het einde kun je als een pro bladwijzertekst toevoegen. Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

-  Aspose.Words voor .NET: Als u het nog niet hebt geïnstalleerd, kunt u[download het hier](https://releases.aspose.com/words/net/).
- Ontwikkelomgeving: Een .NET-ontwikkelomgeving zoals Visual Studio.
- Basiskennis van C#: Kennis van de basisconcepten van C#-programmering is nuttig.
- Word-document met bladwijzers: een Word-document met bladwijzers waaraan we tekst willen toevoegen.

## Importeer noodzakelijke naamruimten

Eerst moeten we de vereiste naamruimten importeren om toegang te krijgen tot de Aspose.Words-functionaliteiten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Stap 1: Laad het document en initialiseer variabelen

Laten we beginnen met het laden van onze bron- en doel-Word-documenten en het initialiseren van de benodigde variabelen.

```csharp
// Laad de bron- en doeldocumenten.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initialiseer de documentimporter.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Zoek de bladwijzer in het brondocument.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Stap 2: Identificeer de begin- en eindalinea's

Vervolgens moeten we de paragrafen vinden waar de bladwijzer begint en eindigt. Dit is essentieel voor het extraheren van de juiste tekst.

```csharp
// Identificeer de paragrafen aan het begin en einde van de bladwijzer.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Valideer de paragrafen.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Stap 3: Valideer de paragrafenouders

We moeten ervoor zorgen dat zowel de begin- als eindparagrafen dezelfde bovenliggende node delen. Dit is een vereenvoudigde aanpak om complicaties te voorkomen.

```csharp
// Controleer of de begin- en eindalinea's dezelfde bovenliggende alinea hebben.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Stap 4: Identificeer het knooppunt dat gestopt moet worden

Nu moeten we bepalen waar we moeten stoppen met het kopiëren van tekst. Dit is het knooppunt direct na de laatste alinea.

```csharp
// Identificeer het knooppunt direct na de laatste alinea.
Node endNode = endPara.NextSibling;
```

## Stap 5: Voeg bladwijzertekst toe aan het doeldocument

Ten slotte doorlopen we de knooppunten van de beginalinea tot het knooppunt na de eindalinea en voegen we deze toe aan het doeldocument.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Importeer het huidige knooppunt in het doeldocument.
    Node newNode = importer.ImportNode(curNode, true);

    // Voeg het geïmporteerde knooppunt toe aan het doeldocument.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Sla het bijgewerkte doeldocument op.
dstDoc.Save("appended_document.docx");
```

## Conclusie

Gefeliciteerd! U hebt succesvol tekst toegevoegd uit een bladwijzersectie in een Word-document met Aspose.Words voor .NET. Deze krachtige bibliotheek maakt documentmanipulatie eenvoudig en nu hebt u een andere handige vaardigheid in uw gereedschapskist. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik tekst uit meerdere bladwijzers tegelijk toevoegen?
Ja, u kunt het proces voor elke bladwijzer herhalen en indien nodig tekst toevoegen.

### Wat als de begin- en eindalinea's verschillende ouders hebben?
In het huidige voorbeeld wordt ervan uitgegaan dat ze dezelfde ouder hebben. Als dat niet zo is, moet u complexere afhandeling implementeren.

### Blijft de originele opmaak van de bijgevoegde tekst behouden?
 Absoluut! Gebruik`ImportFormatMode.KeepSourceFormatting` zorgt ervoor dat de originele opmaak behouden blijft.

### Is het mogelijk om tekst toe te voegen aan een specifieke positie in het doeldocument?
Ja, u kunt tekst toevoegen aan elke gewenste positie door naar het juiste knooppunt in het doeldocument te navigeren.

### Kan ik tekst uit een bladwijzer toevoegen aan een nieuwe sectie?
Ja, u kunt een nieuwe sectie in het doeldocument maken en de tekst daar toevoegen.