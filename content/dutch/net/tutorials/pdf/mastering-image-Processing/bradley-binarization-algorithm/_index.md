---
title: Bradley Binarisatie-algoritme
linktitle: Bradley Binarisatie-algoritme
second_title: Aspose.PDF voor .NET API-referentie
description: Leer hoe u PDF-pagina's kunt converteren naar binaire TIFF-afbeeldingen van hoge kwaliteit met behulp van het bradley-binarisatiealgoritme in Aspose.PDF voor .NET. Deze stapsgewijze handleiding bevat een codevoorbeeld.
type: docs
weight: 30
url: /nl/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Invoering

In deze tutorial leiden we u door het proces van het converteren van een PDF-pagina naar een TIFF-afbeelding met behulp van het Bradley Binarization Algorithm. Aspose.PDF voor .NET vereenvoudigt deze taak, zodat u uw documentworkflows eenvoudig kunt automatiseren en stroomlijnen.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

-  Aspose.PDF voor .NET: Download de bibliotheek van[hier](https://releases.aspose.com/pdf/net/).
- Visual Studio (of een andere C# IDE).
- Basiskennis van C#.
-  Een geldig rijbewijs of een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) van Aspose.

## Stap 1: Stel uw project in

Maak eerst een nieuw C#-project in uw IDE en importeer de benodigde naamruimten:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Stap 2: Definieer de documentdirectory

Geef het pad op naar de map waarin uw PDF-document zich bevindt, evenals de uitvoerpaden voor de TIFF-afbeeldingen:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Pad naar uw PDF-bestand
```

In deze map worden zowel de bron-PDF als de geconverteerde TIFF-bestanden opgeslagen.

## Stap 3: Het PDF-document laden

Open het PDF-document dat u wilt converteren:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Vervangen`PageToTIFF.pdf` met de naam van uw PDF-bestand.

## Stap 4: Uitvoerpaden specificeren

Definieer de uitvoerpaden voor de gegenereerde TIFF-bestanden:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Stap 5: Stel de beeldresolutie in

Stel de resolutie in voor de TIFF-afbeeldingen. Een hogere DPI levert een betere beeldkwaliteit op:

```csharp
Resolution resolution = new Resolution(300);
```

## Stap 6: TIFF-instellingen configureren

Configureer de instellingen voor de TIFF-afbeelding, inclusief compressie en kleurdiepte:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Met 1 bpp (1 bit per pixel) wordt de afbeelding voorbereid voor binaire uitvoer.

## Stap 7: Het TIFF-apparaat maken

Maak een TIFF-apparaat dat de conversie afhandelt:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Stap 8: Converteer de PDF-pagina naar TIFF

Converteer de eerste pagina van de PDF naar een TIFF-afbeelding:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Stap 9: Pas het Bradley Binarisatie-algoritme toe

Pas nu het Bradley-algoritme toe om de grijswaarden TIFF-afbeelding om te zetten in een binaire afbeelding:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 De`BinarizeBradley` methode neemt twee bestandsstromen (invoer en uitvoer) en een drempelwaarde. Pas de drempelwaarde indien nodig aan voor optimale resultaten.

## Stap 10: Bevestig succesvolle conversie

Bevestig ten slotte dat de conversie succesvol was:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Conclusie

Gefeliciteerd! U hebt met succes een PDF-pagina omgezet in een TIFF-afbeelding en het Bradley Binarization Algorithm toegepast met Aspose.PDF voor .NET. Dit proces is essentieel voor documentarchivering, OCR en andere professionele toepassingen. Met een hoge resolutie en efficiënte compressie zijn uw documentafbeeldingen helder en beheersbaar qua formaat.

## Veelgestelde vragen

### Wat is het Bradley-algoritme?
Het Bradley-algoritme is een binarisatietechniek die grijswaardenafbeeldingen omzet in binaire afbeeldingen door voor elke pixel een adaptieve drempelwaarde te bepalen op basis van de omgeving.

### Kan ik met deze methode meerdere PDF-pagina's naar TIFF converteren?
 Ja, u kunt de`Process` Methode om alle pagina's in het document te doorlopen voor conversie.

### Wat is de optimale resolutie voor het converteren van PDF's naar TIFF?
Voor afbeeldingen van hoge kwaliteit wordt doorgaans een resolutie van 300 DPI aanbevolen, maar u kunt dit naar eigen wens aanpassen.

### Wat betekent 1bpp in kleurdiepte?
bpp (1 bit per pixel) geeft aan dat de afbeelding zwart-wit is, waarbij elke pixel volledig zwart of volledig wit is.

### Is het Bradley-algoritme geschikt voor OCR?
Ja, het Bradley-algoritme wordt vaak gebruikt bij OCR-voorverwerking omdat het het tekstcontrast in gescande documenten verbetert en zo de herkenningsnauwkeurigheid verbetert.