---
title: Een nieuwe digitale handtekening toevoegen aan een ondertekend Excel-bestand
linktitle: Een nieuwe digitale handtekening toevoegen aan een ondertekend Excel-bestand
second_title: Aspose.Cells .NET Excel-verwerkings-API
description: Leer hoe u een nieuwe digitale handtekening toevoegt aan een bestaand ondertekend Excel-bestand met Aspose.Cells voor .NET. Deze uitgebreide gids behandelt alle vereisten, stapsgewijze instructies en een codevoorbeeld.
type: docs
weight: 12
url: /nl/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Invoering

In het digitale landschap van vandaag de dag is het belangrijker dan ooit om de authenticiteit en integriteit van documenten te waarborgen. Digitale handtekeningen bieden een betrouwbare manier om te verifiëren dat een document niet is gewijzigd en dat het afkomstig is van een legitieme bron. Als u met Excel-bestanden in .NET werkt en een nieuwe digitale handtekening aan een bestand moet toevoegen dat al is ondertekend, dan is deze gids iets voor u! We leiden u door het proces van het toevoegen van een digitale handtekening aan een bestaand ondertekend Excel-bestand met behulp van Aspose.Cells voor .NET.

## Vereisten

Voordat we met de implementatie beginnen, moet u ervoor zorgen dat u over het volgende beschikt:

1.  Aspose.Cells voor .NET: Download en installeer Aspose.Cells van de[vrijgavepagina](https://releases.aspose.com/cells/net/).
2. .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd en dat u bekend bent met de basisprincipes van .NET-programmering.
3. Digitaal certificaat: verkrijg een geldig digitaal certificaat in .pfx-formaat. Voor het testen kunt u een zelfondertekend certificaat maken.
4. Ontwikkelomgeving: Gebruik een IDE zoals Visual Studio om uw C#-code te schrijven en uit te voeren.
5. Voorbeeld Excel-bestand: U hebt een bestaand Excel-bestand dat al digitaal is ondertekend en waaraan u een nieuwe handtekening wilt toevoegen.

Nu deze voorwaarden vervuld zijn, kunnen we aan de slag met de code!

## Importeer benodigde pakketten

Voeg bovenaan uw C#-bestand de volgende naamruimten toe om toegang te krijgen tot de vereiste klassen en methoden:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Stap 1: Definieer uw mappen

Geef de mappen voor uw bronbestanden op en waar u het uitvoerbestand wilt opslaan:

```csharp
// Bron directory
string sourceDir = "Your Document Directory"; // Vervang door uw eigen directory
// Uitvoermap
string outputDir = "Your Document Directory"; // Vervang door uw eigen directory
```

## Stap 2: Laad de bestaande ondertekende werkmap

Laad de Excel-werkmap die al is ondertekend:

```csharp
// Laad de werkmap die al digitaal is ondertekend
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Stap 3: Maak een digitale handtekeningencollectie

Maak een verzameling om uw digitale handtekeningen te beheren:

```csharp
//Creëer de digitale handtekeningencollectie
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Stap 4: Laad uw certificaat

Laad uw digitale certificaat, dat gebruikt zal worden om de nieuwe handtekening te creëren:

```csharp
// Certificaatbestand en het wachtwoord ervan
string certFileName = sourceDir + "AsposeDemo.pfx"; // Uw certificaatbestand
string password = "aspose"; // Uw certificaatwachtwoord

// Nieuw certificaat aanmaken
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Stap 5: Maak een nieuwe digitale handtekening

Maak nu een nieuwe digitale handtekening en voeg deze toe aan uw verzameling:

```csharp
// Maak een nieuwe digitale handtekening en voeg deze toe aan de verzameling
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Stap 6: Voeg de handtekeningenverzameling toe aan de werkmap

Voeg de digitale handtekeningenverzameling toe aan de werkmap:

```csharp
// Digitale handtekeningenverzameling toevoegen aan de werkmap
workbook.AddDigitalSignature(dsCollection);
```

## Stap 7: Sla de werkmap op

Sla de werkmap op met de nieuwe digitale handtekening:

```csharp
// Werkmap opslaan
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Stap 8: Bevestig succes

Geef feedback bij succesvolle uitvoering:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Conclusie

Gefeliciteerd! U hebt met succes een nieuwe digitale handtekening toegevoegd aan een reeds ondertekend Excel-bestand met Aspose.Cells voor .NET. Dit proces verbetert de beveiliging van uw documenten en verzekert hun authenticiteit en integriteit.

## Veelgestelde vragen

### Wat is een digitale handtekening?

Een digitale handtekening is een wiskundig systeem waarmee de authenticiteit en integriteit van digitale berichten of documenten wordt gecontroleerd. Hiermee wordt gewaarborgd dat deze niet zijn gewijzigd en wordt de identiteit van de ondertekenaar bevestigd.

### Heb ik een speciaal certificaat nodig om een digitale handtekening te maken?

Ja, voor het maken van een geldige digitale handtekening is een digitaal certificaat vereist dat is uitgegeven door een vertrouwde certificeringsinstantie (CA).

### Kan ik een zelfondertekend certificaat gebruiken voor testen?

Absoluut! U kunt een zelfondertekend certificaat gebruiken voor ontwikkelings- en testdoeleinden, maar voor productie is het raadzaam om een certificaat van een vertrouwde CA te gebruiken.

### Wat gebeurt er als ik een handtekening probeer toe te voegen aan een niet-ondertekend document?

Als u probeert een digitale handtekening toe te voegen aan een document dat nog niet is ondertekend, werkt dat zonder problemen. De originele handtekening is echter niet aanwezig.

### Waar kan ik meer informatie vinden over Aspose.Cells?

 Voor gedetailleerde handleidingen en API-referenties, raadpleeg de[Aspose.Cells-documentatie](https://reference.aspose.com/cells/net/).