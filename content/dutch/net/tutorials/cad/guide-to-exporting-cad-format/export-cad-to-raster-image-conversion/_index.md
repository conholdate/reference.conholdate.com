---
title: Exporteer CAD naar rasterafbeeldingconversie met Aspose.CAD voor .NET
linktitle: CAD exporteren naar rasterafbeeldingconversie
second_title: Aspose.CAD .NET - CAD- en BIM-bestandsindeling
description: Leer hoe u CAD-lay-outs efficiënt kunt converteren naar verschillende rasterafbeeldingsformaten met Aspose.CAD voor .NET. Deze uitgebreide gids leidt u door het proces met duidelijke code.
type: docs
weight: 10
url: /nl/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Invoering

Wilt u CAD-lay-outs moeiteloos omzetten naar rasterafbeeldingsformaten met Aspose.CAD voor .NET? Deze stapsgewijze handleiding is ontworpen om u te helpen door het proces te navigeren, compleet met beknopte codefragmenten voor een soepele ervaring. Of u nu een ervaren ontwikkelaar bent of net begint, deze tutorial biedt waardevolle inzichten voor alle vaardigheidsniveaus.

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u begint:

-  Aspose.CAD voor .NET-bibliotheek: Download en installeer de bibliotheek van de[Aspose.CAD-website](https://releases.aspose.com/cad/net/).
-  CAD-tekeningbestand: Zorg dat u uw CAD-tekeningbestand (bijv.`conic_pyramid.dxf`) klaar voor conversie.

## Vereiste naamruimten importeren

In uw .NET-project moet u de benodigde naamruimten importeren om Aspose.CAD-functies te gebruiken. Voeg het volgende toe aan de bovenkant van uw code:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Stap 1: Laad uw CAD-tekening

Geef eerst de directory op en laad uw CAD-bestand in een Image-instantie:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// CAD-tekening laden
using (var image = Image.Load(sourceFilePath))
{
    // Ga door naar de volgende stappen
}
```

## Stap 2: Rasteropties maken

Stel vervolgens de rasteropties in en definieer de gewenste afmetingen voor de uitvoerafbeelding:

```csharp
// Initialiseer CadRasterizationOptions
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Stap 3: Lagen voor conversie specificeren

Als u specifieke lagen wilt converteren, voegt u deze toe aan uw rasteropties:

```csharp
// Geef de laag op die u wilt converteren
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Stap 4: Stel JPEG-exportopties in

Maak nu opties voor het afbeeldingsformaat waarnaar u wilt exporteren (in dit geval JPEG):

```csharp
// Maak JpegOptions voor export
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Stap 5: Exporteren naar JPEG-formaat

Sla ten slotte de geconverteerde afbeelding op:

```csharp
// Definieer het pad van het uitvoerbestand en sla de afbeelding op
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Extra functie: alle lagen converteren

Om alle lagen in uw CAD-tekening te converteren, kunt u de volgende methode implementeren:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Doorloop de lagen en sla ze elk op als een afzonderlijk JPEG-bestand
    // Uw implementatiecode hier
}
```

## Conclusie

Gefeliciteerd! U hebt geleerd hoe u CAD-lay-outs effectief kunt converteren naar rasterafbeeldingsformaten met Aspose.CAD voor .NET. Deze handleiding biedt een eenvoudige aanpak die geschikt is voor ontwikkelaars die streven naar efficiënte CAD-conversies.

## Veelgestelde vragen

### Kan ik exporteren naar verschillende afbeeldingsformaten?

 Absoluut! Gewoon omwisselen`JpegOptions` met andere opmaakopties, zoals`PngOptions` of`BmpOptions`, afhankelijk van uw behoeften.

### Is er een proefversie beschikbaar?

 Ja, u kunt een proefversie downloaden om de functionaliteit te verkennen door dit te volgen[link](https://releases.aspose.com/cad/net/).

### Waar kan ik ondersteuning vinden voor Aspose.CAD?

 Voor community-ondersteuning, bekijk Aspose.CAD[forum](https://forum.aspose.com/c/cad/19), of overweeg om een licentie aan te schaffen voor meer specifieke assistentie.

### Zijn tijdelijke vergunningen mogelijk?

 Ja, tijdelijke licenties zijn beschikbaar; u kunt er een aanvragen[hier](https://purchase.conholdate.com/temporary-license/).

### Waar kan ik gedetailleerde documentatie vinden?

 Bezoek de uitgebreide documentatie[hier](https://reference.aspose.com/cad/net/) voor meer informatie.