---
title: Een inhoudsopgave toevoegen aan een PDF-document
linktitle: Een inhoudsopgave toevoegen aan een PDF-document
second_title: Aspose.PDF voor .NET API-referentie
description: In deze zelfstudie leert u hoe u een inhoudsopgave (TOC) aan een PDF-document toevoegt met behulp van Aspose.Pdf voor .NET.
type: docs
weight: 40
url: /nl/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Invoering

Het maken van een inhoudsopgave (TOC) in een PDF-document kan de navigatie en toegankelijkheid ervan aanzienlijk verbeteren. In deze handleiding laten we zien hoe u een TOC toevoegt aan een PDF-bestand met Aspose.Pdf voor .NET.

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u begint:

1.   Aspose.PDF voor .NET: Download en installeer de nieuwste versie van[hier](https://releases.aspose.com/pdf/net/).
2.  Ontwikkelomgeving: Stel een .NET-ontwikkelomgeving in, zoals Visual Studio.
3.   Licentie: Vraag indien nodig een tijdelijke licentie aan; ga naar[Aspose.Pdf-licentiepagina](https://asposepdf.com/developers) voor meer informatie.

Importeren van benodigde bibliotheken

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Stap 1: Het PDF-document laden

Laad uw bestaande PDF-bestand waar u de TOC wilt toevoegen. Geef het pad naar uw documentdirectory op.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Stap 2: Voeg een nieuwe pagina in voor de inhoudsopgave

Voeg een nieuwe pagina in aan het begin van het PDF-document. Deze pagina zal dienen als de inhoudsopgave (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Stap 3: Maak een TOC-informatieobject

Maak een object dat de TOC-informatie vertegenwoordigt. Voeg een titel en link ernaar toe voor betere navigatie.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Stap 4: Definieer TOC-elementen

Definieer de elementen (of koppen) die in de TOC worden weergegeven. Deze elementen kunnen lezers helpen navigeren naar specifieke secties van het document.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Stap 5: Maak TOC-koppen

Maak koppen voor de eerste twee elementen in de TOC. Deze koppen linken naar hun respectievelijke pagina's.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Stap 6: Sla de PDF op met de inhoudsopgave

Sla ten slotte het bijgewerkte PDF-bestand op.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Bevestigingsbericht

Geef een bevestigingsbericht weer om de gebruiker te laten weten dat het proces is voltooid.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Conclusie

Met Aspose.PDF voor .NET is het toevoegen van een inhoudsopgave aan een PDF niet alleen eenvoudig, maar ook aanpasbaar. Of u nu eenvoudige navigatielinks of complexe structuren wilt maken, deze tool heeft het voor u. Dus vergeet niet om de volgende keer dat u aan een lange PDF werkt, een inhoudsopgave toe te voegen voor een professionele touch.

## Veelgestelde vragen

### Kan ik het uiterlijk van de inhoudsopgave in Aspose.PDF aanpassen?

Ja, u kunt het uiterlijk van de inhoudsopgave volledig aanpassen, inclusief het lettertype, de grootte en de uitlijning.

### Hoe voeg ik subkoppen toe aan de inhoudsopgave?

 kunt subkoppen toevoegen door de`Heading` niveau (bijv.`Heading(2)`).

### Is het mogelijk om de inhoudsopgave automatisch bij te werken als het document verandert?

Nee, de TOC wordt niet automatisch bijgewerkt. U moet deze opnieuw maken als de documentstructuur verandert.

### Kan ik inhoudsopgavevermeldingen koppelen aan externe documenten?

Ja, u kunt hyperlinks gebruiken om inhoudsopgave-items te koppelen aan externe PDF's of URL's.

### Ondersteunt Aspose.PDF inhoudsopgaven met meerdere niveaus?

Ja, Aspose.PDF ondersteunt inhoudsopgaven op meerdere niveaus voor complexe documenten met subsecties.
