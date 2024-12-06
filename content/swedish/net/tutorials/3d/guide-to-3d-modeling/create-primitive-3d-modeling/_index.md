---
title: Skapa primitiv 3D-modellering
linktitle: Skapa primitiv 3D-modellering
second_title: Aspose.3D .NET API
description: Lär dig hur du skapar och anpassar primitiva 3D-modeller, inklusive lådor och cylindrar, och sparar dem i FBX-format utan ansträngning.
type: docs
weight: 10
url: /sv/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Introduktion

Välkommen till den uppslukande världen av 3D-modellering med Aspose.3D för .NET! I denna omfattande handledning guidar vi dig genom processen att skapa primitiva 3D-modeller steg för steg. Oavsett om du är en erfaren utvecklare eller nybörjare som vill lära dig, kommer den här guiden att ge dig möjlighet att skapa visuellt fantastiska 3D-element för dina projekt.

## Förutsättningar

Innan du dyker in i 3D-modellering, se till att du har följande förutsättningar på plats:

-  Aspose.3D for .NET: Ladda ner och installera Aspose.3D for .NET-biblioteket från[nedladdningssida](https://releases.aspose.com/3d/net/).
  
- .NET-utvecklingsmiljö: Konfigurera en miljö som är kompatibel med Aspose.3D, som Visual Studio.

Med allt förberett, låt oss ge oss ut på vårt 3D-modelleringsäventyr!

## Importera nödvändiga namnområden

Börja med att importera de nödvändiga namnområdena för att komma åt Aspose.3D-funktioner:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Dessa namnutrymmen ger dig de verktyg som krävs för att manipulera 3D-modeller och spara dina skapelser.

## Steg 1: Initiera ett scenobjekt

Skapa ett nytt scenobjekt som fungerar som arbetsytan för dina 3D-modeller:

```csharp
// Initiera ett scenobjekt
Scene scene = new Scene();
```

Den här scenen kommer att innehålla de primitiva former du håller på att skapa.

## Steg 2: Skapa en boxmodell

Låt oss sedan lägga till en boxmodell till din scen:

```csharp
// Skapa en Box-modell
scene.RootNode.CreateChildNode("box", new Box());
```

Du kan anpassa lådans dimensioner och egenskaper för att passa din kreativa vision.

## Steg 3: Skapa en cylindermodell

Förbättra nu din scen genom att lägga till en cylinder:

```csharp
// Skapa en cylindermodell
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Precis som med lådan, justera gärna cylinderns parametrar för att uppnå önskat utseende.

## Steg 4: Spara scenen i FBX-format

För att bevara din 3D-modell, spara den i FBX-format:

```csharp
// Spara ritningen i FBX-format
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Se till att välja en lämplig utdatakatalog och filnamn för din modell.

## Steg 5: Visa ett framgångsmeddelande

Till sist, fira din framgång genom att visa ett meddelande:

```csharp
// Visa framgångsmeddelande
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Din 3D-scen som består av primitiva modeller är nu komplett och sparad!

## Slutsats

 Grattis till att du skapat fantastiska 3D-modeller med Aspose.3D för .NET! Denna handledning täckte grunderna i primitiv modellering, men möjligheterna är oändliga. Utforska mer om avancerade funktioner och tekniker i[dokumentation](https://reference.aspose.com/3d/net/).

## FAQ's

### Kan jag använda Aspose.3D för .NET med andra programmeringsspråk än .NET?

Aspose.3D stöder huvudsakligen .NET, men det finns versioner tillgängliga för Java och andra plattformar.

### Finns det en gratis provperiod?

 Ja, du kan prova Aspose.3D:s funktioner med en[gratis provperiod](https://releases.aspose.com/).

### Var kan jag hitta stöd för Aspose.3D för .NET?

För samhällsstöd, besök[Aspose.3D-forum](https://forum.aspose.com/c/3d/18).

### Hur kan jag få en tillfällig licens?

 Du kan begära en tillfällig licens[här](https://purchase.conholdate.com/temporary-license/).

### Finns det ytterligare tutorials tillgängliga?

 Ja! Utforska fler handledningar och exempel i[dokumentation](https://reference.aspose.com/3d/net/).