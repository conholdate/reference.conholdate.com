---
title: Gegevens kopiëren binnen Excel-werkmap met Aspose.Cells voor .NET
linktitle: Gegevens kopiëren binnen Excel-werkmap met Aspose.Cells voor .NET
second_title: Aspose.Cells .NET Excel-verwerkings-API
description: Leer hoe u efficiënt gegevens kopieert binnen een Excel-werkmap met Aspose.Cells voor .NET. Volg deze stapsgewijze handleiding om eenvoudig bladen te dupliceren, gegevens over te brengen en Excel-bestanden eenvoudig te beheren.
type: docs
weight: 12
url: /nl/net/tutorials/cells/mastering-worksheet-value-operations/copy-data-within-excel-workbook/
---
## Invoering

In deze gedetailleerde handleiding laten we zien hoe u gegevens binnen dezelfde werkmap kopieert met Aspose.Cells voor .NET. Door de onderstaande stapsgewijze instructies te volgen, leert u hoe u bladen programmatisch dupliceert, waarbij de inhoud en opmaak behouden blijven.

## Vereisten voor het kopiëren van gegevens in Excel met Aspose.Cells

Voordat we beginnen met coderen, moeten we ervoor zorgen dat alles op orde is:

1. Aspose.Cells voor .NET-bibliotheek: U moet de Aspose.Cells voor .NET-bibliotheek geïnstalleerd hebben. U kunt de nieuwste versie downloaden van de[Aspose.Cells voor .NET downloadpagina](https://releases.aspose.com/cells/net/).
2. Ontwikkelomgeving: Een .NET-compatibele IDE zoals Visual Studio is nodig om uw code te schrijven en uit te voeren.
3.  Aspose-licentie: U kunt een gratis proefversie of een gekochte licentie gebruiken. Ga voor meer informatie naar[hier](https://purchase.aspose.com/temporary-license/).

Zodra de vereisten zijn ingesteld, kunt u met de bibliotheek aan de slag.

## Vereiste pakketten importeren

Om te beginnen moet u de relevante naamruimten importeren uit Aspose.Cells. Hiermee kunt u met Excel-bestanden werken met behulp van de klassen en methoden die door Aspose.Cells worden geleverd.

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

 Deze naamruimten geven u toegang tot de`Workbook` klasse (voor het werken met Excel-bestanden) en`WorksheetCollection` (voor toegang tot meerdere bladen in een werkmap).

## Stap 1: Initialiseer bestandspaden voor werkmap

Om uw code georganiseerd te houden, is het essentieel om de bestandspaden te definiëren waar uw werkmap zich bevindt en waar u het gewijzigde bestand wilt opslaan. Hier ziet u hoe u de paden kunt opgeven:

```csharp
// Definieer het pad naar de map waar het Excel-bestand zich bevindt.
string dataDir = "Your Directory Path";

// Definieer het volledige pad naar de invoerwerkmap.
string inputPath = dataDir + "book1.xls";
```

 Vervangen`"Your Directory Path"` met het werkelijke pad naar uw directory met de werkmap. Dit helpt ervoor te zorgen dat de code flexibel is en dat u paden effectief kunt beheren.

## Stap 2: Open de werkmap om toegang te krijgen tot gegevens

 Nu de bestandspaden zijn ingesteld, is de volgende stap het laden van de Excel-werkmap in een`Workbook` object. Hiermee kunt u de inhoud ervan benaderen voor manipulatie.

```csharp
// Laad het Excel-bestand in het werkmapobject.
Workbook wb = new Workbook(inputPath);
```

 Met deze regel hebt u succesvol geladen`book1.xls` in de`wb` object, waardoor de gegevens ervan toegankelijk worden.

## Stap 3: Toegang tot de werkbladencollectie

 Zodra de werkmap is geladen, hebt u toegang tot de bladen die erin zijn opgenomen. Aspose.Cells biedt de`Worksheets`verzameling, waarmee u met elk werkblad in de werkmap kunt werken.

```csharp
// Haal de verzameling werkbladen op uit de werkmap.
WorksheetCollection sheets = wb.Worksheets;
```

 De`sheets` object geeft u nu toegang tot alle werkbladen binnen`book1.xls`en u kunt er verschillende bewerkingen mee uitvoeren, waaronder het kopiëren van gegevens van het ene werkblad naar het andere.

## Stap 4: Gegevens van het ene blad naar het andere kopiëren

 Om gegevens van het ene werkblad naar het andere binnen dezelfde werkmap te kopiëren, biedt Aspose.Cells een eenvoudig te gebruiken methode genaamd`AddCopy`Met deze methode wordt een duplicaat van het opgegeven werkblad gemaakt en aan de werkmap toegevoegd.

```csharp
// Kopieer gegevens van 'Blad1' naar een nieuw blad in de werkmap.
sheets.AddCopy("Sheet1");
```

 In dit voorbeeld kopiëren we gegevens van "Sheet1" naar een nieuw werkblad.`AddCopy` Met deze methode wordt het hele werkblad gedupliceerd, waarbij de volledige inhoud behouden blijft, inclusief formules, opmaak en waarden.

## Stap 5: Sla de aangepaste werkmap op

 Nadat u de gegevens hebt gekopieerd, kunt u de gewijzigde werkmap opslaan met een nieuwe naam of locatie. Dit doet u door de`Save`methode op de`Workbook` voorwerp.

```csharp
//Sla de gewijzigde werkmap op onder een nieuwe naam.
wb.Save(dataDir + "book1_copy.xls");
```

 Hiermee wordt de werkmap met het gekopieerde werkblad opgeslagen als`book1_copy.xls` in de opgegeven directory. U kunt de bestandsnaam en het pad naar wens wijzigen.

## Conclusie

Gegevens kopiëren binnen een Excel-werkmap met Aspose.Cells voor .NET is een eenvoudige taak en deze handleiding biedt de stappen die nodig zijn om dit efficiënt te doen. Of u nu hele bladen of specifieke gegevensbereiken dupliceert, Aspose.Cells biedt een robuuste en flexibele API die Excel-automatisering eenvoudig en effectief maakt.

## Veelgestelde vragen

### Kan ik meerdere vellen tegelijk kopiëren?

Aspose.Cells ondersteunt het kopiëren van meerdere sheets in één enkele aanroep niet. U kunt echter wel door de sheets heen lopen die u wilt kopiëren en ze afzonderlijk kopiëren.

### Hoe kan ik de naam van het gekopieerde werkblad wijzigen?

Nadat u het werkblad hebt gekopieerd, kunt u het als volgt hernoemen:

```csharp
sheets[sheets.Count - 1].Name = "NewSheetName";
```

### Is Aspose.Cells compatibel met .NET Core?

Ja, Aspose.Cells is volledig compatibel met zowel .NET Framework- als .NET Core-omgevingen.

### Hoe gaat Aspose.Cells om met opmaak tijdens het kopiëren?

 De`AddCopy`Met deze methode blijven alle inhoud en opmaak behouden bij het kopiëren van bladen, zodat de gekopieerde gegevens er identiek uitzien als het origineel.

### Kan ik een werkblad naar een andere werkmap kopiëren?

 Ja, u kunt een werkblad naar een andere werkmap kopiëren met behulp van de`Copy` methode met een verwijzing naar de doelwerkmap.

```csharp
sheets.Add().Copy(wb.Worksheets["Sheet1"]);
```