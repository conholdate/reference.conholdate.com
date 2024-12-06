---
title: Pagina opslaan Callback in Word-documenten
linktitle: Pagina opslaan Callback in Word-documenten
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u eenvoudig elke pagina van een Word-document kunt converteren naar afzonderlijke PNG-afbeeldingen met Aspose.Words voor .NET. Deze handleiding biedt stapsgewijze instructies, inclusief codevoorbeelden.
type: docs
weight: 10
url: /nl/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Invoering

Heb je ooit elke pagina van een Word-document moeten omzetten in afzonderlijke afbeeldingen? Of je nu miniaturen wilt maken voor een preview of een lang rapport wilt opsplitsen in verteerbare beelden, Aspose.Words voor .NET maakt deze taak eenvoudig en efficiënt. In deze handleiding leiden we je door het proces van het instellen van een pagina-opslaande callback om elke pagina van je document op te slaan als een PNG-afbeelding. Laten we beginnen!

## Vereisten

Zorg ervoor dat u het volgende bij de hand hebt voordat u aan de slag gaat:

1.  Aspose.Words voor .NET: Download en installeer het vanaf[hier](https://releases.aspose.com/words/net/).
2. Visual Studio: elke versie is geschikt, maar voor deze handleiding gebruiken we Visual Studio 2019.
3. Basiskennis van C#: Als u bekend bent met C#, kunt u de cursus soepel volgen.

## Stap 1: Importeer de benodigde naamruimten

Eerst moeten we de vereiste namespaces importeren. Dit stelt ons in staat om toegang te krijgen tot de benodigde klassen en methoden zonder dat we telkens de volledige namespace hoeven te typen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Stap 2: Definieer uw documentendirectory

Stel vervolgens het pad in naar uw documentdirectory. Dit is waar uw invoer-Word-document zich bevindt en waar de uitvoerafbeeldingen worden opgeslagen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Stap 3: Laad uw document

Laten we nu het document laden dat u wilt verwerken. Zorg ervoor dat uw document, genaamd "Rendering.docx," zich in de opgegeven directory bevindt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Stap 4: Configureer de opties voor het opslaan van afbeeldingen

We stellen de opties voor het opslaan van afbeeldingen in en geven aan dat we de pagina's als PNG-bestanden willen opslaan.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Hier,`PageSet` definieert het bereik van de pagina's die moeten worden opgeslagen, en`PageSavingCallback` verwijst naar onze aangepaste callbackklasse.

## Stap 5: Implementeer de paginabesparende callback

Nu moeten we de callbackklasse implementeren die regelt hoe elke pagina wordt opgeslagen.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Deze klasse implementeert de`IPageSavingCallback` interface. In de`PageSaving` Met deze methode specificeren we het naamgevingspatroon voor elke opgeslagen pagina.

## Stap 6: Sla het document op als afbeeldingen

Tot slot slaan we het document op met behulp van de geconfigureerde opties.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusie

Gefeliciteerd! U hebt met succes een pagina-opslaande callback ingesteld om elke pagina van een Word-document op te slaan als een afzonderlijke PNG-afbeelding met behulp van Aspose.Words voor .NET. Deze techniek is ongelooflijk nuttig voor verschillende toepassingen, van het maken van paginavoorbeelden tot het genereren van afzonderlijke pagina-afbeeldingen voor rapporten.

## Veelgestelde vragen

### Kan ik pagina's opslaan in andere formaten dan PNG?
 Ja! U kunt pagina's opslaan informaten zoals JPEG, BMP en TIFF door de`SaveFormat` in `ImageSaveOptions`.

### Hoe kan ik alleen specifieke pagina's opslaan?
 Om specifieke pagina's op te slaan, past u de`PageSet` parameter in`ImageSaveOptions` om alleen de gewenste pagina's op te nemen.

### Is het mogelijk om de beeldkwaliteit aan te passen?
 Absoluut! U kunt de kwaliteit van de uitvoerafbeelding regelen door eigenschappen in te stellen zoals`ImageSaveOptions.JpegQuality`.

### Hoe kan ik grote documenten efficiënt verwerken?
Bij grote documenten kunt u overwegen om pagina's in batches te verwerken, zodat u het geheugengebruik effectief kunt beheren.

### Waar kan ik meer informatie vinden over Aspose.Words voor .NET?
 Voor uitgebreide handleidingen en voorbeelden, bekijk de[Aspose.Words-documentatie](https://reference.aspose.com/words/net/).