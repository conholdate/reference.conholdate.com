---
title: Gevulde rechthoek maken
linktitle: Gevulde rechthoek maken
second_title: Aspose.PDF voor .NET API-referentie
description: Ontgrendel de kracht van PDF-manipulatie met Aspose.PDF voor .NET in deze stapsgewijze tutorial. Leer hoe u programmatisch visueel aantrekkelijke PDF-documenten maakt door gevulde rechthoeken te tekenen.
type: docs
weight: 50
url: /nl/net/tutorials/pdf/mastering-Graph-programming/creating-filled-rectangle/
---
## Invoering

Heb je ooit visueel verbluffende PDF's willen maken via een programma? Dan ben je hier aan het juiste adres! In deze tutorial verkennen we Aspose.PDF voor .NET, een krachtige bibliotheek die PDF-documentmanipulatie vereenvoudigt. Vandaag richten we ons op het maken van een gevulde rechthoek in een PDF-bestand. Of je nu een doorgewinterde ontwikkelaar bent of net begint, deze gids leidt je op een vriendelijke en boeiende manier door elke stap. Dus pak je codeerhoed en laten we beginnen!

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u het volgende heeft:

1. Visual Studio: Installeer Visual Studio op uw computer, want het is een uitstekende IDE voor .NET-ontwikkeling.
2. Aspose.PDF voor .NET: Download en installeer de Aspose.PDF-bibliotheek van[hier](https://releases.aspose.com/pdf/net/).
3. Basiskennis van C#: Kennis van C#-programmering helpt u de codefragmenten beter te begrijpen.

## Stap 1: Maak een nieuw project

1. Open Visual Studio en maak een nieuw Console Application-project.
2. Geef uw project een passende naam.

## Stap 2: Voeg Aspose.PDF-referentie toe

1. Klik met de rechtermuisknop op uw project in de Solution Explorer.
2. Selecteer NuGet-pakketten beheren.
3. Zoek naar Aspose.PDF en installeer de nieuwste versie.

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

Nu we alles hebben ingesteld, kunnen we beginnen met de code!

## Stap 3: Stel uw documentenmap in

Geef het pad op waar uw PDF moet worden opgeslagen:

```csharp
// Het pad naar de documentenmap.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Vervangen`"YOUR DOCUMENT DIRECTORY"` met het daadwerkelijke pad op uw computer waar u de PDF wilt opslaan.

## Stap 4: Een documentinstantie maken

Initialiseer een nieuw PDF-document:

```csharp
//Documentinstantie maken
Document doc = new Document();
```

## Stap 5: Een pagina toevoegen aan het document

Elke PDF heeft minimaal één pagina nodig. Laten we er één toevoegen:

```csharp
// Pagina toevoegen aan paginaverzameling van PDF-bestand
Page page = doc.Pages.Add();
```

## Stap 6: Een grafiekinstantie maken

 A`Graph` Het is bijvoorbeeld een canvas waarop je vormen kunt tekenen:

```csharp
// Grafiekinstantie maken
Aspose.Pdf.Drawing.Graph graph = new Aspose.Pdf.Drawing.Graph(100.0, 400.0);
```

## Stap 7: Voeg de grafiek toe aan de pagina

Voeg de grafiek toe aan de pagina:

```csharp
// Grafiekobject toevoegen aan alineaverzameling van pagina-instantie
page.Paragraphs.Add(graph);
```

## Stap 8: Maak een rechthoekinstantie

Definieer de positie en grootte van de rechthoek:

```csharp
// Maak een rechthoek-instantie
Aspose.Pdf.Drawing.Rectangle rect = new Aspose.Pdf.Drawing.Rectangle(100, 100, 200, 120);
```

## Stap 9: Geef de vulkleur op

Kies een kleur voor uw rechthoek. Voor dit voorbeeld gebruiken we rood:

```csharp
// Vulkleur voor grafiekobject opgeven
rect.GraphInfo.FillColor = Aspose.Pdf.Color.Red;
```

## Stap 10: Voeg de rechthoek toe aan de grafiek

Voeg de rechthoek toe aan de grafiek:

```csharp
// Rechthoekig object toevoegen aan vormenverzameling van Grafiekobject
graph.Shapes.Add(rect);
```

## Stap 11: Sla het PDF-document op

Sla ten slotte uw document op in de opgegeven directory:

```csharp
dataDir = dataDir + "CreateFilledRectangle_out.pdf";
// PDF-bestand opslaan
doc.Save(dataDir);
```

## Stap 12: Bevestigingsbericht

Druk een bevestigingsbericht af om aan te geven dat het gelukt is:

```csharp
Console.WriteLine("\nFilled rectangle object created successfully.\nFile saved at " + dataDir);
```

## Conclusie

Gefeliciteerd! U hebt met succes een gevulde rechthoek in een PDF-document gemaakt met Aspose.PDF voor .NET. Deze krachtige bibliotheek opent een wereld aan mogelijkheden voor PDF-manipulatie, zodat u verbluffende documenten programmatisch kunt genereren. Of u nu rapporten, facturen of een ander type PDF maakt, Aspose.PDF heeft alles wat u nodig hebt.

## Veelgestelde vragen

### Wat is Aspose.PDF voor .NET?
Aspose.PDF voor .NET is een bibliotheek waarmee ontwikkelaars programmatisch PDF-documenten kunnen maken, bewerken en converteren.

### Kan ik Aspose.PDF gratis gebruiken?
 Ja, Aspose biedt een gratis proefversie die u kunt gebruiken om de functies van de bibliotheek te verkennen. U kunt deze downloaden[hier](https://releases.aspose.com/).

### Is er een manier om ondersteuning te krijgen voor Aspose.PDF?
 Absoluut! Je kunt ondersteuning krijgen via het Aspose forum[hier](https://forum.aspose.com/c/pdf/10).

### Hoe kan ik Aspose.PDF kopen?
 U kunt Aspose.PDF kopen door de aankooppagina te bezoeken[hier](https://purchase.aspose.com/buy).

### Welke soorten vormen kan ik maken met Aspose.PDF?
Met de Aspose.PDF-bibliotheek kunt u verschillende vormen maken, waaronder rechthoeken, cirkels, lijnen en meer.