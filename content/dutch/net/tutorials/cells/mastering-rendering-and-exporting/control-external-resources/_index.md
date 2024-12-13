---
title: Beheer externe bronnen met Aspose.Cells voor .NET
linktitle: Beheer externe bronnen met Aspose.Cells voor .NET
second_title: Aspose.Cells .NET Excel-verwerkings-API
description: Ontgrendel het volledige potentieel van uw Excel naar PDF conversies met Aspose.Cells voor .NET. In deze uitgebreide gids leert u hoe u externe bronnen, zoals afbeeldingen, beheert en ervoor zorgt dat uw PDF's uw exacte opmaakvereisten weerspiegelen.
type: docs
weight: 12
url: /nl/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Invoering

In het digitale landschap van vandaag is het converteren van Excel-spreadsheets naar PDF-documenten een veelvoorkomende en essentiële taak. Of u nu rapporten, financiële gegevens of presentatiematerialen voorbereidt, het is cruciaal om ervoor te zorgen dat uw PDF's het gewenste formaat weergeven. Aspose.Cells voor .NET biedt een krachtige bibliotheek waarmee u dit conversieproces tot in detail kunt beheren, vooral bij het werken met externe bronnen zoals afbeeldingen. In deze handleiding onderzoeken we hoe u externe bronnen effectief kunt beheren tijdens het conversieproces van Excel naar PDF met Aspose.Cells. Laten we erin duiken!

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende bij de hand hebt:

1. Visual Studio of een andere .NET-compatibele IDE: Dit wordt uw ontwikkelomgeving.
2.  Aspose.Cells voor .NET: Als u het nog niet hebt geïnstalleerd, bezoek dan de[Aspose-downloads](https://releases.aspose.com/cells/net/) pagina om de nieuwste versie te verkrijgen.
3. Basiskennis van C#: Kennis van C# is nuttig. Als u verduidelijking nodig hebt over concepten, kunt u ze gerust opzoeken.
4. Voorbeeld Excel-bestand: Maak een Excel-bestand, zoals 'samplePdfSaveOptions_StreamProvider.xlsx', dat de externe bronnen bevat die u wilt converteren.
5. Afbeeldingsbestand voor testen: Gebruik een afbeeldingsbestand zoals "newPdfSaveOptions_StreamProvider.png" als externe bron tijdens de conversie.

## Importeer benodigde pakketten

Om te beginnen moet u de vereiste naamruimten importeren uit de Aspose.Cells-bibliotheek. Voeg het volgende toe met behulp van richtlijnen boven aan uw C#-bestand:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Deze naamruimten bieden de essentiële klassen en methoden voor uw taken.

## Stap 1: Een streamproviderklasse maken

 Maak eerst een streamproviderklasse die de`IStreamProvider` interface. Met deze klasse kunt u bepalen hoe externe bronnen worden geladen.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Laad de afbeelding in een geheugenstroom
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Deze methode wordt aangeroepen wanneer de stream gesloten is en er momenteel een foutopsporingsbericht wordt geregistreerd.
- InitStream: Deze methode leest het externe afbeeldingsbestand als een byte-array, converteert het naar een geheugenstroom en wijst het toe aan de`options.Stream` eigendom.

## Stap 2: Bron- en uitvoermappen instellen

Definieer vervolgens de mappen voor uw Excel-bestand en de uitvoer-PDF.

```csharp
// Bron directory
string sourceDir = "Your Document Directory";
// Uitvoermap
string outputDir = "Your Document Directory";
```

 Vervangen`"Your Document Directory"` met het daadwerkelijke pad op uw systeem waar uw bestanden zich bevinden.

## Stap 3: Laad uw Excel-bestand

Laad nu het Excel-bestand waarvan u de PDF wilt maken.

```csharp
// Laad het bron-Excelbestand met externe afbeeldingen
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 De`Workbook` klasse van Aspose.Cells vertegenwoordigt uw Excel-bestand, dat verschillende externe bronnen zoals afbeeldingen kan bevatten.

## Stap 4: PDF-opslagopties instellen

Voordat u de werkmap als PDF opslaat, geeft u de gewenste opslagopties op.

```csharp
// Geef PDF-opslagopties op - Streamprovider
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Sla elk blad op een nieuwe pagina op
};
```

 Dit creëert een instantie van`PdfSaveOptions` , waarmee u het PDF-formaat kunt aanpassen. De`OnePagePerSheet` Met deze optie wordt ervoor gezorgd dat elk Excel-werkblad op een aparte pagina in de uiteindelijke PDF wordt weergegeven.

## Stap 5: Wijs uw streamprovider toe

 Verbind uw`Workbook` bijvoorbeeld met de`MyStreamProvider` klasse die u eerder hebt gemaakt.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Deze regel zorgt ervoor dat wanneer er tijdens de conversie externe bronnen worden aangetroffen, uw aangepaste provider deze dienovereenkomstig beheert.

## Stap 6: Sla de werkmap op als PDF

Sla uw Excel-werkmap nu op als PDF.

```csharp
// Sla de werkmap op als PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Door de`Save` Door de methode op het werkmapobject uit te voeren en de uitvoermap samen met de PDF-opties door te geven, converteert u het Excel-bestand naar een correct opgemaakte PDF.

## Stap 7: Bevestig succesvolle uitvoering

Ten slotte is het een goed idee om te controleren of het proces succesvol is afgerond.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Met dit bericht wordt u geïnformeerd over de status van uw bewerking en krijgt u nuttige feedback.

## Conclusie

beheerst nu het proces van het beheren van externe bronnen tijdens Excel naar PDF conversies met Aspose.Cells! Door deze stappen te volgen, kunt u ervoor zorgen dat uw documenten nauwkeurig afbeeldingen en andere externe elementen bevatten, wat elke keer resulteert in een gepolijst eindproduct.

## Veelgestelde vragen

### Wat is Aspose.Cells?
Aspose.Cells is een krachtige bibliotheek voor .NET-ontwikkelaars waarmee u Excel-bestanden in verschillende formaten kunt maken, bewerken, converteren en weergeven.

### Hoe download ik Aspose.Cells?
 U kunt de nieuwste versie downloaden van de[Downloadlink](https://releases.aspose.com/cells/net/).

### Kan ik Aspose.Cells gratis uitproberen?
 Ja! U kunt een gratis proefperiode krijgen door naar de website te gaan[Gratis proefpagina](https://releases.aspose.com/).

### Waar kan ik ondersteuning vinden voor Aspose.Cells?
 Voor vragen over ondersteuning kunt u terecht op de[Aspose Ondersteuningsforum](https://forum.aspose.com/c/cells/9).

### Hoe kan ik een tijdelijke licentie voor Aspose.Cells verkrijgen?
 U kunt een tijdelijke vergunning aanvragen[hier](https://purchase.aspose.com/temporary-license/).
