---
title: Beheer de zichtbaarheid van bladwijzers in Word-documenten
linktitle: Beheer de zichtbaarheid van bladwijzers in Word-documenten
second_title: Aspose.Words API voor documentverwerking
description: Ontdek hoe u de zichtbaarheid van content in Word-documenten vakkundig kunt beheren met Aspose.Words voor .NET. Deze stapsgewijze handleiding.
type: docs
weight: 10
url: /nl/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Invoering

Bent u klaar om uw documentmanipulatievaardigheden te verbeteren met Aspose.Words voor .NET? Of u nu een ervaren ontwikkelaar bent die documenttaken automatiseert of een nieuwsgierig persoon die programmatische controle over Word-bestanden verkent, deze gids is op maat gemaakt voor u. Vandaag duiken we in hoe u inhoud kunt weergeven en verbergen op basis van bladwijzers in een Word-document. Laten we beginnen!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1. Visual Studio: elke versie die compatibel is met .NET.
2. Aspose.Words voor .NET: Download het[hier](https://releases.aspose.com/words/net/).
3. Basiskennis van C#: Kennis van het schrijven van eenvoudige C#-programma's is voldoende.
4. Een voorbeeld van een Word-document: Maak een Word-document (bijvoorbeeld 'Bladwijzers.docx') met bladwijzers voor deze tutorial.

### Een nieuw project maken

1. Open Visual Studio en maak een nieuw Console App (.NET Core)-project. Geef het een naam als 'BookmarkVisibilityManager'.

### Installeer Aspose.Words voor .NET

Voeg Aspose.Words toe aan uw project via NuGet Package Manager:

1. Ga naar Extra > NuGet Package Manager > NuGet-pakketten beheren voor oplossing.
2. Zoek naar "Aspose.Words".
3. Installeer het pakket.

Nu uw project is ingesteld, kunt u het document laden.

## Naamruimten importeren

Begin met het importeren van de essentiële naamruimten. Deze bieden de klassen en methoden die nodig zijn voor het manipuleren van Word-documenten met Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Stap 1: Het document laden

Om het Word-document te manipuleren, moeten we het eerst laden. Dit is hoe je dat doet:

```csharp
// Definieer het pad naar uw documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Met dit fragment wordt het pad naar uw documentmap ingesteld en wordt het document in een map geladen.`Document` voorwerp.

## Stap 2: Toon/verberg gemarkeerde inhoud

 Laten we nu een methode maken om de zichtbaarheid van content te wisselen op basis van bladwijzers. We noemen deze methode`ShowHideBookmarkedContent`.

Dit is de implementatie van de methode:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Bladwijzer ophalen:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` haalt de opgegeven bladwijzer op.
- Knooppunttraversal: We itereren door de knooppunten binnen de bladwijzer.
-  Zichtbaarheidsschakelaar: Voor elk`Run` knooppunt (dat een tekstsegment vertegenwoordigt), stellen we de`Hidden` eigendom gebaseerd op de`isHidden` parameter.

## Stap 3: De methode toepassen

Nu we onze methode gereed hebben, kunnen we deze gebruiken om inhoud binnen een specifieke bladwijzer weer te geven of te verbergen:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Verbergt inhoud binnen "MyBookmark1"
```

Met deze regel verbergt u de inhoud die is gekoppeld aan de bladwijzer met de naam "MyBookmark1".

## Stap 4: Het document opslaan

Nadat u uw wijzigingen hebt aangebracht, vergeet dan niet het gewijzigde document op te slaan:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Hiermee wordt het document opgeslagen met de bijgewerkte zichtbaarheidsinstellingen.

## Conclusie

Gefeliciteerd! U hebt succesvol geleerd hoe u bladwijzerinhoud in een Word-document kunt weergeven en verbergen met Aspose.Words voor .NET. Deze krachtige bibliotheek vereenvoudigt documentmanipulatie, waardoor het ideaal is voor het automatiseren van rapporten, het maken van sjablonen of het experimenteren met Word-bestanden. Veel plezier met coderen!

## Veelgestelde vragen

### Kan ik meerdere bladwijzers tegelijk in- en uitschakelen?
 Ja, bel gewoon de`ShowHideBookmarkedContent` methode voor elke bladwijzer die u wilt in- of uitschakelen.

### Heeft het verbergen van inhoud invloed op de structuur van het document?
Nee, als u inhoud verbergt, heeft dat alleen invloed op de zichtbaarheid ervan. De inhoud blijft intact in het document.

### Kan ik deze methode gebruiken voor andere soorten content?
Deze methode is speciaal ontworpen voor tekstruns. Voor andere contenttypen moet u de node traversal-logica dienovereenkomstig aanpassen.

### Is Aspose.Words voor .NET gratis?
 Aspose.Words biedt een gratis proefperiode aan[hier](https://releases.aspose.com/) , maar voor productiegebruik is een volledige licentie vereist. U kunt het kopen[hier](https://purchase.aspose.com/buy).

### Hoe kan ik ondersteuning krijgen als ik problemen ondervind?
 Voor ondersteuning kunt u terecht op het Aspose communityforum[hier](https://forum.aspose.com/c/words/8).