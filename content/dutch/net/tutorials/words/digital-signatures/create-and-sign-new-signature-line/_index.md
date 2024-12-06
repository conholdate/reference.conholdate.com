---
title: Maak en onderteken een nieuwe handtekeningregel
linktitle: Maak en onderteken een nieuwe handtekeningregel
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u naadloos een digitale handtekening toevoegt aan uw Word-documenten met Aspose.Words voor .NET. Deze uitgebreide tutorial behandelt alles van het instellen van uw omgeving en het invoegen van een handtekeningregel tot het opslaan en verifiëren van uw ondertekende documenten.
type: docs
weight: 10
url: /nl/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Invoering

Wilt u een digitale handtekening toevoegen aan een Word-document? Met Aspose.Words voor .NET is het eenvoudiger dan u denkt! Deze tutorial leidt u door de stappen van het instellen van uw omgeving, het toevoegen van een handtekeningregel en het digitaal ondertekenen van uw document. Laten we beginnen!

## Vereisten

Voordat u de code induikt, moet u ervoor zorgen dat u het volgende hebt:

1.  Aspose.Words voor .NET -[Download het hier](https://releases.aspose.com/words/net/).
2. .NET Development Environment - Visual Studio is ideaal voor deze taak.
3. Te ondertekenen document - U kunt een nieuw Word-document maken of een bestaand document gebruiken.
4.  Certificaatbestand - A`.pfx` bestand is nodig voor digitale handtekeningen.
5. Afbeelding handtekeningregel (optioneel) - U kunt een afbeeldingbestand voor de handtekening bijvoegen.

## Vereiste naamruimten importeren

Om de functionaliteiten van Aspose.Words te gebruiken, moet u de volgende naamruimten importeren:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Stap 1: De documentenmap instellen

Begin met het definiëren van het pad naar uw documentdirectory. Dit is waar u uw documenten opslaat en ophaalt.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Geef het pad naar uw documentdirectory op
```

## Stap 2: Een nieuw document maken

Laten we nu een nieuw Word-document maken. Dit document zal dienen als canvas voor uw handtekeningregel.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 3: De handtekeningregel invoegen

 Gebruik nu de`DocumentBuilder` klasse om een handtekeningregel in uw document in te voegen:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Stap 4: Het document opslaan

Zodra u de handtekeningregel hebt ingevoegd, slaat u het document op. Dit is een cruciale stap voordat u ondertekent.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Stap 5: Ondertekeningsopties configureren

Stel de opties in voor het ondertekeningsproces. Dit omvat het specificeren van de handtekeningregel-ID en de optionele afbeelding die bij de handtekening moet worden weergegeven.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Pad naar uw afbeelding
};
```

## Stap 6: Het certificaat laden

Laad het certificaatbestand dat nodig is voor het ondertekenen van het document:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Bestandsnaam en wachtwoord aanpassen
```

## Stap 7: Het document ondertekenen

 Onderteken ten slotte het document met de`DigitalSignatureUtil` klasse. Sla het ondertekende document op met een nieuwe naam voor toekomstige referentie.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Conclusie

Gefeliciteerd! U hebt met succes een Word-document gemaakt, een handtekeningregel toegevoegd en het digitaal ondertekend met Aspose.Words voor .NET. Deze krachtige tool vereenvoudigt documentautomatisering en zorgt ervoor dat uw contracten en formele documenten veilig worden ondertekend en geverifieerd.

## Veelgestelde vragen

### Kan ik andere afbeeldingsformaten gebruiken voor de handtekeningregel?

Ja, u kunt verschillende afbeeldingsformaten gebruiken, waaronder PNG, JPG en BMP.

###  Is het nodig om een`.pfx` file for the certificate?

 Ja, een`.pfx` bestand is een standaardformaat voor het opslaan van certificaten en persoonlijke sleutels voor digitale handtekeningen.

### Kan ik meerdere handtekeningregels in één document toevoegen?

Absoluut! U kunt meerdere handtekeningregels invoegen door de invoegstap indien nodig te herhalen.

### Wat als ik geen digitaal certificaat heb?

U moet een digitaal certificaat aanvragen bij een vertrouwde certificeringsinstantie of er zelf een genereren met behulp van hulpmiddelen zoals OpenSSL.

### Hoe verifieer ik de digitale handtekening in het document?

U kunt de digitale handtekening verifiëren door het ondertekende document in Word te openen en de handtekeningdetails te controleren om de authenticiteit en integriteit ervan te bevestigen.