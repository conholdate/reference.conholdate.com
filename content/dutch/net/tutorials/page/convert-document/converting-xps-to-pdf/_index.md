---
title: XPS naar PDF converteren met Aspose.Page voor .NET
linktitle: XPS naar PDF converteren
second_title: Aspose.Pagina .NET API
description: Ontdek hoe u XPS-documenten (XML Paper Specification) naadloos kunt converteren naar PDF (Portable Document Format) met behulp van de krachtige Aspose.Page voor .NET-bibliotheek.
type: docs
weight: 11
url: /nl/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Invoering

In deze tutorial gaan we onderzoeken hoe u XPS (XML Paper Specification) documenten kunt converteren naar PDF (Portable Document Format) met behulp van de veelzijdige Aspose.Page voor .NET bibliotheek. Deze krachtige bibliotheek vereenvoudigt documentconversie en biedt verschillende aanpassingsopties, waardoor het een uitstekende keuze is voor ontwikkelaars.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende geregeld hebt:

-  Aspose.Page voor .NET-bibliotheek: Download en installeer de Aspose.Page voor .NET-bibliotheek van de[Aspose.Page-documentatie](https://reference.aspose.com/page/net/).
  
- Ontwikkelomgeving: Stel een .NET-ontwikkelomgeving in met Visual Studio of een andere compatibele IDE.

- XPS-document: Zorg dat het XPS-bestand dat u wilt converteren gereed is en opgeslagen is in een aangewezen map.

## Stap 1: Importeer vereiste naamruimten

Begin met het importeren van de benodigde naamruimte om toegang te krijgen tot de Aspose.Page-functionaliteiten:

```csharp
using Aspose.Page.XPS;
```

## Stap 2: Documentdirectory initialiseren

Definieer het directorypad waar uw documenten zijn opgeslagen:

```csharp
string dataDir = "Your Document Directory";
```

 Zorg ervoor dat u vervangt`"Your Document Directory"` met het werkelijke pad naar de map met uw XPS-document.

### Stap 3: Open PDF- en XPS-streams

Initialiseer vervolgens de streams voor zowel het invoer-XPS-bestand als het uitvoer-PDF-bestand:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Zorg ervoor dat u het juiste pad voor uw bestanden hebt ingesteld.

### Stap 4: Laad het XPS-document

Laad nu uw XPS-document met behulp van de Aspose.Page-bibliotheek:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Stap 5: PDF-opslagopties configureren

Stel de opslagopties voor uw PDF in, inclusief de afbeeldingskwaliteit en compressieparameters:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Stel het JPEG-kwaliteitsniveau in
    ImageCompression = PdfImageCompression.Jpeg, // Gebruik JPEG-compressie voor afbeeldingen
    TextCompression = PdfTextCompression.Flate, // Flate-compressie toepassen op tekst
    PageNumbers = new int[] { 1, 2, 6 } // Geef paginanummers op die u wilt opnemen
};
```

U kunt deze parameters naar eigen wens aanpassen.

### Stap 6: Het PDF-renderingapparaat maken

Maak een renderingapparaat voor het PDF-formaat:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Stap 7: Sla het document op als PDF

Sla ten slotte het XPS-document op als PDF-bestand met behulp van het opgegeven apparaat en de opgegeven opties:

```csharp
document.Save(device, options);
```

## Conclusie

Gefeliciteerd! U hebt met succes een XPS-document naar PDF geconverteerd met Aspose.Page voor .NET. Deze bibliotheek vereenvoudigt niet alleen documentconversie, maar biedt ook uitgebreide mogelijkheden voor het verwerken van verschillende formaten.

## Veelgestelde vragen

### Kan ik meerdere XPS-bestanden naar één PDF converteren?

Absoluut! U kunt door meerdere XPS-bestanden itereren en ze samenvoegen tot één PDF-document door dezelfde conversiestappen te volgen.

### Welke andere uitvoerformaten ondersteunt Aspose.Page voor .NET?

Naast PDF ondersteunt Aspose.Page voor .NET een reeks formaten, waaronder TIFF, JPEG en PNG.

### Hoe kan ik het uiterlijk van de geconverteerde PDF aanpassen?

 U kunt de parameters in de`PdfSaveOptions` object, zoals JPEG-kwaliteit en compressie-instellingen, om het gewenste uiterlijk te bereiken.

### Is er een proefversie beschikbaar voor Aspose.Page voor .NET?

Ja, u kunt Aspose.Page voor .NET uitproberen met een gratis proefversie die beschikbaar is[hier](https://releases.aspose.com/).

### Waar kan ik communityondersteuning vinden voor Aspose.Page voor .NET?

 Voor discussies en ondersteuning in de gemeenschap, bezoek de[Aspose.Page-forum](https://forum.aspose.com/c/page/39).