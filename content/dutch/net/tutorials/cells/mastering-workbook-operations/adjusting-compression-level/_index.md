---
title: Compressieniveau in werkmap aanpassen
linktitle: Compressieniveau in werkmap aanpassen
second_title: Aspose.Cells .NET Excel-verwerkings-API
description: Ontdek hoe u efficiënt grote Excel-bestanden kunt beheren door compressieniveaus aan te passen met Aspose.Cells voor .NET. Deze stapsgewijze handleiding behandelt alles van het instellen van mappen tot het meten van compressietijden, en helpt u de bestandsgrootte te optimaliseren en de prestaties te verbeteren.
type: docs
weight: 14
url: /nl/net/tutorials/cells/mastering-workbook-operations/adjusting-compression-level/
---
## Invoering

Het beheren van grote Excel-bestanden kan een uitdaging zijn, vooral als het gaat om opslag- en overdrachtsefficiëntie. Gelukkig kan bestandscompressie de grootte van deze bestanden aanzienlijk verkleinen, waardoor ze gemakkelijker te hanteren zijn. Als u Aspose.Cells voor .NET gebruikt, kunt u het compressieniveau van uw werkmappen eenvoudig aanpassen. Deze gids leidt u stap voor stap door het proces en biedt duidelijke uitleg over elk onderdeel van de code.

## Vereisten

Voordat we in de code duiken, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

1. Basiskennis van C#: Kennis van C#-programmering helpt u de codefragmenten beter te begrijpen.
2.  Aspose.Cells-bibliotheek: Download en installeer de Aspose.Cells-bibliotheek van[hier](https://releases.aspose.com/cells/net/).
3. Visual Studio: Een ontwikkelomgeving zoals Visual Studio is nodig om de code uit te voeren.
4. .NET Framework: Zorg ervoor dat uw project is ingesteld met een compatibele versie van .NET Framework.

## Noodzakelijke pakketten importeren

Om te beginnen moet u de benodigde pakketten importeren in uw C#-project. Voeg de volgende regels toe bovenaan uw codebestand:

```csharp
using Aspose.Cells.Rendering;
using Aspose.Cells.WebExtensions;
using System;
```

 Deze pakketten zijn essentieel voor het werken met Excel-bestanden met behulp van de Aspose.Cells-bibliotheek.`Aspose.Cells` naamruimte bevat alle klassen die nodig zijn om Excel-bestanden te manipuleren, terwijl`Aspose.Cells.Xlsb` biedt opties voor het opslaan van bestanden in XLSB-formaat.

## Stap 1: Definieer bron- en uitvoermappen

Stel eerst de mappen in waar uw bronbestanden zich bevinden en waar u de uitvoerbestanden wilt opslaan:

```csharp
// Definieer bron- en uitvoermappen
string sourceDir = "Your Document Directory\\";
string outDir = "Your Document Directory\\";
```

 Zorg ervoor dat u vervangt`"Your Document Directory\\"` met de werkelijke paden naar uw mappen. Dit zorgt ervoor dat uw programma de bestanden kan vinden waarmee het moet werken.

## Stap 2: Laad de werkmap

Laad vervolgens de werkmap die u wilt comprimeren:

```csharp
Workbook workbook = new Workbook(sourceDir + "LargeSampleFile.xlsx");
```

 Hier maken we een nieuw exemplaar van de`Workbook` class en laad een bestaand Excel-bestand. Zorg ervoor dat de bestandsnaam overeenkomt met die in uw bronmap.

## Stap 3: Stel opslagopties in

Configureer nu de opslagopties voor uw werkmap:

```csharp
XlsbSaveOptions options = new XlsbSaveOptions();
```

 De`XlsbSaveOptions`Met de klasse kunt u verschillende opties opgeven wanneer u uw werkmap opslaat in de XLSB-indeling, waaronder compressieniveaus.

## Stap 4: Meet de compressietijd voor niveau 1

Begin met het eerste compressieniveau en meet de tijd die nodig is om de werkmap op te slaan:

```csharp
options.CompressionType = OoxmlCompressionType.Level1;
var watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_1_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 1 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Met dit fragment wordt het compressietype ingesteld op Niveau 1, wordt de werkmap opgeslagen en wordt de verstreken tijd gemeten.

## Stap 5: Meet de compressietijd voor niveau 6

Test vervolgens de prestaties met Level 6-compressie:

```csharp
options.CompressionType = OoxmlCompressionType.Level6;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_6_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 6 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Deze stap is vergelijkbaar met de vorige, maar met een hoger compressieniveau.

## Stap 6: Meet de compressietijd voor niveau 9

Evalueer ten slotte de prestaties met het hoogste compressieniveau:

```csharp
options.CompressionType = OoxmlCompressionType.Level9;
watch = Stopwatch.StartNew();
workbook.Save(outDir + "LargeSampleFile_level_9_out.xlsb", options);
watch.Stop();
Console.WriteLine("Level 9 Elapsed Time: " + watch.ElapsedMilliseconds + " ms");
```

Met deze stap wordt het compressieniveau ingesteld op niveau 9. Op dit niveau ziet u waarschijnlijk de grootste vermindering van de bestandsgrootte, maar het kan wel langer duren om dit te verwerken.

## Stap 7: Eindresultaat

Nadat alle compressieniveaus zijn voltooid, wordt er een bericht weergegeven waarin staat dat het proces succesvol is voltooid:

```csharp
Console.WriteLine("Compression adjustment completed successfully.");
```

Deze eenvoudige regel bevestigt dat uw programma zonder problemen is uitgevoerd.

## Conclusie

Het aanpassen van het compressieniveau van uw werkmappen met Aspose.Cells voor .NET is een eenvoudig proces dat kan leiden tot aanzienlijke verbeteringen in bestandsgrootte en prestaties. Door de stappen in deze handleiding te volgen, kunt u compressie efficiënt implementeren in uw toepassingen, waardoor uw Excel-bestandsbeheermogelijkheden worden verbeterd.

## Veelgestelde vragen

### Wat is Aspose.Cells?  
Aspose.Cells is een krachtige bibliotheek voor .NET waarmee ontwikkelaars Excel-bestanden kunnen maken, bewerken en converteren zonder dat ze Microsoft Excel nodig hebben.

### Hoe installeer ik Aspose.Cells?  
 U kunt Aspose.Cells downloaden en installeren vanaf de[Aspose-website](https://releases.aspose.com/cells/net/).

### Welke compressieniveaus zijn beschikbaar?  
Aspose.Cells ondersteunt meerdere compressieniveaus, van niveau 1 (laagste compressie) tot en met niveau 9 (hoogste compressie).

### Kan ik Aspose.Cells gratis testen?  
 Ja! U kunt een gratis proefversie van Aspose.Cells krijgen[hier](https://releases.aspose.com/).

### Waar kan ik ondersteuning vinden voor Aspose.Cells?  
 Voor vragen of ondersteuning kunt u terecht op het Aspose-ondersteuningsforum[hier](https://forum.aspose.com/c/cells/9).