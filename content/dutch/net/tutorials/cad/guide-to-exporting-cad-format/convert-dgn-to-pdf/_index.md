---
title: Converteer DGN naar PDF in Aspose.CAD voor .NET
linktitle: Converteer DGN naar PDF in Aspose.CAD voor .NET
second_title: Aspose.CAD .NET - CAD- en BIM-bestandsindeling
description: Leer hoe u moeiteloos DGN-bestanden naar PDF converteert met de krachtige Aspose.CAD-bibliotheek voor .NET. Deze stapsgewijze handleiding is ontworpen voor ontwikkelaars van alle niveaus.
type: docs
weight: 12
url: /nl/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Invoering

Navigeren door de wereld van CAD-bestanden kan een uitdaging zijn, maar met Aspose.CAD voor .NET kunnen ontwikkelaars eenvoudig verschillende CAD-formaten manipuleren en converteren. Een veelvoorkomende behoefte is het converteren van DGN-bestanden naar PDF's, wat we stap voor stap zullen onderzoeken in deze tutorial.

## Vereisten

Om de instructies te kunnen volgen, moet u het volgende bij de hand hebben:

- Basiskennis van C# en het .NET Framework.
-  Aspose.CAD voor .NET-bibliotheek geïnstalleerd. U kunt het downloaden[hier](https://releases.aspose.com/cad/net/).
- Een voorbeeld van een DGN-bestand (bijvoorbeeld Nikon_D90_Camera.dgn). 

## Stap 1: Importeer vereiste naamruimten

Begin met het importeren van de relevante naamruimten in uw C#-project:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Stap 2: Laad het DGN-bestand

Geef de directory voor uw DGN-bestand op en laad het met behulp van de volgende code:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Verdere verwerking vindt hier plaats...
}
```

## Stap 3: Rasteropties configureren

Stel vervolgens de rasteropties in om te definiëren hoe uw DGN in de PDF wordt weergegeven:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Pas de breedte indien nodig aan
    PageHeight = 300, // Pas de hoogte indien nodig aan
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Stap 4: PDF-opties maken

Definieer de PDF-opties en integreer daarbij de eerder geconfigureerde rasterinstellingen:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Stap 5: Sla de DGN op als PDF

Sla ten slotte het DGN-bestand op als PDF met behulp van de opties die u hebt geconfigureerd:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Conclusie

Gefeliciteerd! U hebt met succes een DGN-bestand omgezet naar een PDF met Aspose.CAD voor .NET. Deze eenvoudige tutorial leidde u door het laden van het DGN-bestand, het instellen van rasteropties en het opslaan van de uitvoer als een PDF.

## Veelgestelde vragen

### Heb ik voorkennis van CAD nodig om Aspose.CAD te gebruiken?  
Absoluut! Aspose.CAD is ontworpen om complexe CAD-taken te vereenvoudigen, waardoor het toegankelijk is voor alle ontwikkelaars, ongeacht hun CAD-kennis.

### Waar kan ik meer bronnen en documentatie voor Aspose.CAD vinden?  
 U kunt uitgebreide handleidingen en voorbeelden bekijken in de[Aspose.CAD-documentatie](https://reference.aspose.com/cad/net/).

### Is er een gratis proefversie beschikbaar voor Aspose.CAD?  
 Ja, er kan een gratis proefversie worden verkregen[hier](https://releases.aspose.com/).

### Hoe kan ik een tijdelijke licentie voor Aspose.CAD krijgen?  
 U kunt tijdelijke licenties aanvragen[hier](https://purchase.conholdate.com/temporary-license/).

### Heeft u hulp nodig of vragen?  
Doe mee aan het gesprek in de[Aspose.CAD-forum](https://forum.aspose.com/c/cad/19) voor ondersteuning en vragen van de gemeenschap.