---
title: Voeg teksthandtekeningen toe aan documenten met behulp van GroupDocs.Signature
linktitle: Teksthandtekeningen toevoegen aan documenten
second_title: GroupDocs.Signature .NET API
description: Leer hoe u documenten met tekst ondertekent met GroupDocs.Signature voor .NET. Stapsgewijze handleiding voor het programmatisch toevoegen van teksthandtekeningen.
type: docs
weight: 17
url: /nl/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Invoering

In het digitale landschap van vandaag de dag is elektronische documentondertekening essentieel geworden voor het stroomlijnen van workflows en het besparen van middelen. GroupDocs.Signature voor .NET biedt een krachtige oplossing voor het programmatisch toevoegen van teksthandtekeningen aan verschillende documentformaten. Deze tutorial leidt u door de stappen om een document met tekst te ondertekenen met behulp van GroupDocs.Signature voor .NET.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:

1.  GroupDocs.Signature voor .NET: Download en installeer de bibliotheek van[hier](https://releases.groupdocs.com/signature/net/).
2. Ontwikkelomgeving: Stel uw .NET-ontwikkelomgeving in.
3. Document: Bereid het document voor dat u wilt ondertekenen (bijv. PDF, Word).

## Noodzakelijke naamruimten importeren

Begin met het importeren van de vereiste naamruimten in uw .NET-project:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Stap 1: Laad het document

Begin met het laden van het document dat u wilt ondertekenen:

```csharp
string filePath = "sample.pdf"; // Pad naar uw document
string fileName = Path.GetFileName(filePath);
```

## Stap 2: Definieer het pad van het uitvoerbestand

Stel vervolgens het pad in naar het uitvoerbestand waar het ondertekende document wordt opgeslagen:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Stap 3: Handtekeningopties maken

Configureer de opties voor uw teksthandtekening, waaronder de inhoud, positie, grootte, kleur en lettertype:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, //X-positie
    Top = 200, // Y-positie
    Width = 100, // Breedte van de handtekening
    Height = 30, // Hoogte van de handtekening
    ForeColor = Color.Red, // Tekstkleur
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Lettertype-instellingen
};
```

## Stap 4: Onderteken het document

Gebruik ten slotte GroupDocs.Signature om de teksthandtekening toe te passen en het ondertekende document op te slaan:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Onderteken het document
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Conclusie

In deze tutorial hebben we gedemonstreerd hoe u programmatisch een teksthandtekening aan een document kunt toevoegen met behulp van GroupDocs.Signature voor .NET. Door deze stappen te volgen, kunt u de beveiliging en authenticiteit van uw documenten efficiënt verbeteren.

## Veelgestelde vragen

### Kan ik het uiterlijk van de teksthandtekening aanpassen?
Ja, u kunt verschillende kenmerken, zoals kleur, lettertype, grootte en positie van de teksthandtekening, aanpassen aan uw wensen.

### Is GroupDocs.Signature compatibel met meerdere documentformaten?
Absoluut! GroupDocs.Signature ondersteunt een breed scala aan formaten, waaronder PDF, Word, Excel, PowerPoint en meer.

### Kan ik meerdere teksthandtekeningen aan één document toevoegen?
Ja, u kunt meerdere teksthandtekeningen toevoegen, elk met zijn eigen aanpassingsopties.

### Garandeert GroupDocs.Signature de integriteit van het document na ondertekening?
Ja, de bibliotheek maakt gebruik van robuuste cryptografische algoritmen om de integriteit van documenten te waarborgen en manipulatie na ondertekening te voorkomen.

### Is er een proefversie beschikbaar zodat u het kunt testen voordat u het koopt?
 Ja, u kunt een gratis proefversie downloaden van[hier](https://releases.groupdocs.com/) om de functies te verkennen voordat u tot aankoop overgaat.