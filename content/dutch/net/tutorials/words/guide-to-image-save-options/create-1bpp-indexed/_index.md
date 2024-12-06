---
title: Maak 1Bpp geïndexeerd
linktitle: Maak 1Bpp geïndexeerd
second_title: Aspose.Words API voor documentverwerking
description: Deze handleiding bevat stapsgewijze instructies en voorbeeldcode waarmee u op efficiënte wijze 1Bpp-geïndexeerde afbeeldingen kunt maken voor archivering, afdrukken of ruimtebesparing.
type: docs
weight: 10
url: /nl/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Invoering

Heb je ooit een Word-document moeten omzetten naar een zwart-witafbeelding? Of het nu voor digitale archivering, afdrukken of gewoon om ruimte te besparen is, het omzetten van je documenten naar een 1Bpp geïndexeerde afbeelding kan ongelooflijk nuttig zijn. In deze gids laten we je een eenvoudige methode zien om dit te bereiken met Aspose.Words voor .NET. Laten we beginnen!

## Vereisten

Voordat u de code induikt, moet u ervoor zorgen dat u het volgende hebt:

-  Aspose.Words voor .NET: Download en installeer de bibliotheek van[hier](https://releases.aspose.com/words/net/).
- .NET-ontwikkelomgeving: Hoewel Visual Studio een populaire keuze is, werkt elke IDE die .NET ondersteunt.
- Basiskennis van C#: Kennis van C# is handig, maar we houden het simpel.
- Voorbeeld Word-document: Zorg dat u een document gereed hebt voor conversie.

## Stap 1: Importeer de benodigde naamruimten

Om Aspose.Words te gebruiken, moet u de relevante naamruimten importeren. Dit is essentieel voor toegang tot de klassen en methoden die vereist zijn voor documentmanipulatie.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 2: Stel uw documentenmap in

Geef het pad op naar de map waar uw Word-document is opgeslagen en waar u de geconverteerde afbeelding wilt opslaan.

```csharp
// Pad naar uw documentenmap
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Stap 3: Laad het Word-document

Laad uw Word-document in een`Aspose.Words.Document` object. Met dit object kunt u het document programmatisch manipuleren.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 4: Configureer de opties voor het opslaan van afbeeldingen

 Stel vervolgens de`ImageSaveOptions` om te definiëren hoe het document als afbeelding wordt opgeslagen. We configureren het om op te slaan in PNG-formaat met 1Bpp geïndexeerde kleurmodus.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Converteer alleen de eerste pagina
    ImageColorMode = ImageColorMode.BlackAndWhite, // Instellen op zwart-wit
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Gebruik 1Bpp geïndexeerd formaat
};
```

- SaveFormat.Png: Hiermee geeft u aan dat het uitvoerformaat PNG is.
- PageSet(1): Geeft aan dat alleen de eerste pagina van het document wordt geconverteerd.
- ImageColorMode.BlackAndWhite: zorgt ervoor dat de afbeelding zwart-wit is.
- ImagePixelFormat.Format1bppIndexed: Stelt de pixelindeling in op 1Bpp geïndexeerd, voor optimale ruimte-indeling.

## Stap 5: Sla het document op als een afbeelding

 Gebruik ten slotte de`Save` methode van de`Document` object om de geconverteerde afbeelding op te slaan.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Conclusie

Gefeliciteerd! U hebt met succes een Word-document omgezet naar een 1Bpp geïndexeerde afbeelding met Aspose.Words voor .NET. Deze methode is niet alleen efficiënt, maar helpt u ook om contrastrijke afbeeldingen te maken die geschikt zijn voor verschillende toepassingen. Voel u vrij om deze functionaliteit te integreren in uw projecten. Veel plezier met coderen!

## Veelgestelde vragen

### Wat is een 1Bpp geïndexeerde afbeelding?
Een geïndexeerde afbeelding van 1 Bpp (1 bit per pixel) is een zwart-witafbeeldingsformaat waarbij elke pixel wordt weergegeven door één bit, 0 of 1. Dit formaat is zeer ruimtebesparend en daardoor ideaal voor archivering.

### Kan ik meerdere pagina's van een Word-document tegelijk converteren?
 Ja! Wijzig eenvoudig de`PageSet` eigendom in de`ImageSaveOptions` om meerdere pagina's op te nemen of om het hele document te converteren.

### Heb ik een licentie nodig om Aspose.Words voor .NET te gebruiken?
 Ja, voor volledige functionaliteit is een licentie vereist. U kunt een[tijdelijke licentie hier](https://purchase.aspose.com/temporary-license/).

### Naar welke andere afbeeldingsformaten kan ik mijn Word-document converteren?
 Aspose.Words ondersteunt verschillende formaten, waaronder JPEG, BMP en TIFF. Verander gewoon de`SaveFormat`in de`ImageSaveOptions` naar het door u gewenste formaat.

### Waar kan ik meer documentatie vinden over Aspose.Words voor .NET?
 Voor uitgebreide documentatie, bezoek de[Aspose.Words voor .NET-documentatiepagina](https://reference.aspose.com/words/net/).