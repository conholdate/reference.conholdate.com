---
title: VBA-gebruikersformulieren en macro's overbrengen tussen Excel-werkmappen
linktitle: VBA-gebruikersformulieren en macro's overbrengen tussen Excel-werkmappen
second_title: Aspose.Cells .NET Excel-verwerkings-API
description: Ontgrendel de kracht van Excel-automatisering met deze uitgebreide gids over het overbrengen van VBA-gebruikersformulieren en macro's tussen werkmappen met Aspose.Cells voor .NET. Perfect voor zowel beginners als ervaren ontwikkelaars.
type: docs
weight: 11
url: /nl/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Invoering

Welkom bij uw ultieme gids voor het verbeteren van uw Excel-ervaring met VBA-macro's en gebruikersformulieren! In deze tutorial onderzoeken we hoe u een VBA Macro UserForm Designer van de ene werkmap naar de andere kunt overbrengen met behulp van de krachtige Aspose.Cells voor .NET-bibliotheek. Of u nu een ervaren ontwikkelaar bent of net begint, deze stapsgewijze gids geeft u de kennis om Excel-bestanden programmatisch te verwerken. Klaar om erin te duiken? Laten we beginnen!

## Vereisten
Voordat we beginnen met coderen, willen we ervoor zorgen dat je alles hebt wat je nodig hebt:

1. C#-ontwikkelomgeving: een werkomgeving voor C#-ontwikkeling, waarbij Visual Studio sterk wordt aanbevolen.
2.  Aspose.Cells voor .NET-bibliotheek: zorg ervoor dat u de Aspose.Cells-bibliotheek in uw project integreert. U kunt eenvoudig[download het hier](https://releases.aspose.com/cells/net/).
3. Basiskennis van VBA- en Excel-macro's: Kennis van VBA en de werking van Excel-macro's vergroot uw begrip van deze tutorial.
4. Een Excel-bestand met een gebruikersformulier: Maak of verkrijg een Excel-werkmap met een gebruikersformulier (bij voorkeur met ingeschakelde macro's, zoals`.xlsm` bestanden).

## Vereiste pakketten importeren
Om de functionaliteiten van Aspose.Cells te benutten, neemt u de volgende naamruimten boven aan uw C#-bestand op:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Met deze naamruimten krijgt u toegang tot de krachtige tools die in de Aspose.Cells-bibliotheek zijn ingebouwd.

## Stap 1: Definieer uw bron- en uitvoermappen
Bepaal eerst de locaties van uw bestanden:

```csharp
// Definieer de bron- en uitvoermappen
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Vervang de tijdelijke paden door de daadwerkelijke mappen waarin uw bestanden zijn opgeslagen.

## Stap 2: Maak een lege doelwerkmap
Maak vervolgens een nieuwe werkmap waarin u het gebruikersformulier en de macro's kopieert:

```csharp
// Maak een lege doelwerkmap
Workbook target = new Workbook();
```

Hiermee wordt een lege werkmap geïnitialiseerd, die als canvas dient voor de komende gegevensoverdracht.

## Stap 3: Laad uw sjabloonwerkmap
Laad de werkmap met uw gebruikersformulier en macro's:

```csharp
// Laad het Excel-bestand met het VBA-Macro Designer-gebruikersformulier
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Aanpassen`"sampleDesignerForm.xlsm"` naar de naam van uw eigenlijke bestand.

## Stap 4: Kopieer werkbladen naar de doelwerkmap
Laten we nu de werkbladen van de sjabloon naar de doelwerkmap kopiëren:

```csharp
// Kopieer alle sjabloonwerkbladen naar de doelwerkmap
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Voeg een bericht toe in cel A2 van het doelwerkblad
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Deze code doorloopt elk werkblad in de sjabloon en kopieert het naar de doelwerkmap. Zo worden al uw gegevens naadloos overgedragen.

## Stap 5: VBA-macro's kopiëren uit de sjabloon
Vervolgens kopiëren we de VBA-macro's, inclusief de UserForm Designer-modules, naar de nieuwe werkmap:

```csharp
// Kopieer het VBA-Macro Designer UserForm van sjabloon naar doel
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Kopieer ThisWorkbook modulecode
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Kopieer code en gegevens van andere modules
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Haal de opslag van de gebruikersformulierontwerper op
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Voeg de ontwerpopslag toe aan het doel-VBA-project
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Deze code zorgt ervoor dat niet alleen de code, maar ook het ontwerp van het gebruikersformulier wordt gekopieerd, zodat de functionaliteit van uw macro's behouden blijft.

## Stap 6: Sla de doelwerkmap op
Nadat u het kopieerproces hebt voltooid, slaat u uw nieuwe werkmap op:

```csharp
// Sla de doelwerkmap op
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Wijzig de uitvoerbestandsnaam indien nodig. Deze stap creëert uw aangepaste werkmap gevuld met macro's en gebruikersformulieren.

## Stap 7: Bevestig succes
Druk ten slotte een succesbericht af op de console:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Met deze eenvoudige zin weet u zeker dat uw proces soepel is verlopen: een essentiële bevestiging van uw harde werk!

## Conclusie
Gefeliciteerd! U hebt met succes geleerd hoe u een VBA Macro User Form Designer van de ene werkmap naar de andere kopieert met Aspose.Cells voor .NET. Hoewel het in eerste instantie misschien ontmoedigend lijkt, zult u door oefening vaardiger worden in het manipuleren van werkmappen. Vergeet niet dat coderen draait om experimenteren, dus aarzel niet om verschillende functionaliteiten in uw Excel-bestanden te verkennen. Als u vragen hebt of hulp nodig hebt, zijn de Aspose-forums en -documentatie uitstekende bronnen voor ondersteuning.

## Veelgestelde vragen

### Welke versies van Excel worden door Aspose.Cells ondersteund?
Aspose.Cells ondersteunt verschillende Excel-indelingen, waaronder XLSX, XLSM, CSV en meer.

### Kan ik Aspose.Cells gratis gebruiken?
 Ja! U kunt beginnen met een gratis proefperiode om de bibliotheek te evalueren:[Gratis proefperiode](https://releases.aspose.com/).

### Heb ik Visual Studio nodig om deze code uit te voeren?
Hoewel Visual Studio wordt aanbevolen vanwege de gebruiksvriendelijke functies, volstaat elke C# IDE die .NET-ontwikkeling ondersteunt.

### Waar kan ik meer voorbeelden en documentatie vinden?
 Je kunt de[Aspose.Cells-documentatie](https://reference.aspose.com/cells/net/) voor meer voorbeelden en diepgaande uitleg.

### Hoe los ik problemen op bij het gebruik van Aspose.Cells?
 Je moet de[Aspose Ondersteuningsforum](https://forum.aspose.com/c/cells/9) voor hulp van de community en Aspose-ondersteunend personeel.