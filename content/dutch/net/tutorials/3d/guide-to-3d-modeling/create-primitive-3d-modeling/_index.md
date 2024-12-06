---
title: Primitieve 3D-modellen maken
linktitle: Primitieve 3D-modellen maken
second_title: Aspose.3D .NET API
description: Leer hoe u primitieve 3D-modellen, zoals dozen en cilinders, kunt maken en aanpassen en deze moeiteloos in FBX-formaat kunt opslaan.
type: docs
weight: 10
url: /nl/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Invoering

Welkom in de meeslepende wereld van 3D-modellering met Aspose.3D voor .NET! In deze uitgebreide tutorial leiden we u stap voor stap door het proces van het maken van primitieve 3D-modellen. Of u nu een ervaren ontwikkelaar bent of een beginner die graag wil leren, deze gids stelt u in staat om visueel verbluffende 3D-elementen voor uw projecten te maken.

## Vereisten

Voordat u aan de slag gaat met 3D-modellering, moet u ervoor zorgen dat u aan de volgende vereisten voldoet:

-  Aspose.3D voor .NET: Download en installeer de Aspose.3D voor .NET-bibliotheek van de[downloadpagina](https://releases.aspose.com/3d/net/).
  
- .NET-ontwikkelomgeving: Stel een omgeving in die compatibel is met Aspose.3D, zoals Visual Studio.

Nu alles is voorbereid, kunnen we beginnen aan ons 3D-modelleringsavontuur!

## Vereiste naamruimten importeren

Begin met het importeren van de benodigde naamruimten om toegang te krijgen tot de Aspose.3D-functionaliteiten:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Met deze naamruimten beschikt u over de hulpmiddelen die u nodig hebt om 3D-modellen te bewerken en uw creaties op te slaan.

## Stap 1: Initialiseer een scèneobject

Maak een nieuw scèneobject dat als canvas voor uw 3D-modellen fungeert:

```csharp
// Initialiseer een scèneobject
Scene scene = new Scene();
```

Deze scène bevat de primitieve vormen die u gaat maken.

## Stap 2: Maak een boxmodel

Laten we nu een boxmodel aan uw scène toevoegen:

```csharp
// Maak een Box-model
scene.RootNode.CreateChildNode("box", new Box());
```

U kunt de afmetingen en eigenschappen van de doos aanpassen aan uw creatieve visie.

## Stap 3: Maak een cilindermodel

Verbeter nu uw scène door een cilinder toe te voegen:

```csharp
// Maak een cilindermodel
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Net als bij de doos kunt u de parameters van de cilinder naar wens aanpassen.

## Stap 4: Sla de scène op in FBX-formaat

Om uw 3D-model te bewaren, slaat u het op in de FBX-indeling:

```csharp
// Tekening opslaan in FBX-formaat
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Zorg ervoor dat u een geschikte uitvoermap en bestandsnaam voor uw model kiest.

## Stap 5: Geef een succesbericht weer

Vier ten slotte uw succes door een bericht weer te geven:

```csharp
// Succesbericht weergeven
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Uw 3D-scène, bestaande uit primitieve modellen, is nu voltooid en opgeslagen!

## Conclusie

 Gefeliciteerd met het maken van verbluffende 3D-modellen met Aspose.3D voor .NET! Deze tutorial behandelde de basis van primitieve modellering, maar de mogelijkheden zijn eindeloos. Ontdek meer over geavanceerde functies en technieken in de[documentatie](https://reference.aspose.com/3d/net/).

## Veelgestelde vragen

### Kan ik Aspose.3D voor .NET gebruiken met andere programmeertalen dan .NET?

Aspose.3D ondersteunt voornamelijk .NET, maar er zijn versies beschikbaar voor Java en andere platformen.

### Is er een gratis proefperiode beschikbaar?

 Ja, u kunt de mogelijkheden van Aspose.3D uitproberen met een[gratis proefperiode](https://releases.aspose.com/).

### Waar kan ik ondersteuning vinden voor Aspose.3D voor .NET?

Voor ondersteuning van de gemeenschap, bezoek de[Aspose.3D-forum](https://forum.aspose.com/c/3d/18).

### Hoe kan ik een tijdelijk rijbewijs krijgen?

 U kunt een tijdelijke vergunning aanvragen[hier](https://purchase.conholdate.com/temporary-license/).

### Zijn er aanvullende tutorials beschikbaar?

 Ja! Ontdek meer tutorials en voorbeelden in de[documentatie](https://reference.aspose.com/3d/net/).