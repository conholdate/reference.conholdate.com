---
title: Lokale hyperlink maken in PDF-bestand
linktitle: Lokale hyperlink maken in PDF-bestand
second_title: Aspose.PDF voor .NET API-referentie
description: Ontdek hoe u de navigatie in uw PDF-documenten kunt verbeteren door lokale hyperlinks te maken met Aspose.PDF voor .NET. Deze stapsgewijze tutorial leidt u door het hele proces.
type: docs
weight: 40
url: /nl/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Invoering

In deze gids leiden we u door het proces van het maken van lokale hyperlinks in een PDF-bestand met Aspose.PDF voor .NET. We zullen elke stap duidelijk uiteenzetten, zodat u het moeiteloos kunt volgen, zelfs als u nieuw bent in PDF-manipulatie.

## Vereisten

Voordat u de code induikt, moet u ervoor zorgen dat u het volgende hebt:

1.  Visual Studio: Download het van de[Visual Studio-website](https://visualstudio.microsoft.com/).
2.  Aspose.PDF voor .NET: Download de bibliotheek via de[Aspose-website](https://releases.aspose.com/pdf/net/)Deze bibliotheek biedt een uitgebreide set functies voor PDF-manipulatie.
3. Basiskennis van C#: Kennis van C#-programmering is handig, maar maak je geen zorgen: we leggen de code regel voor regel uit.
4. .NET Framework: Zorg ervoor dat u het .NET Framework op uw machine hebt geïnstalleerd. Controleer de vereisten op de Aspose.PDF[documentatie](https://reference.aspose.com/pdf/net/).

Nu u aan deze vereisten voldoet, bent u klaar om te leren hoe u lokale hyperlinks in uw PDF-documenten kunt maken!

## Vereiste pakketten importeren

Nu alles is ingesteld, is het tijd om de benodigde pakketten in uw C#-project te importeren.

### Open uw project

Open uw bestaande .NET-project of maak een nieuw project in Visual Studio. Als u helemaal opnieuw begint, selecteert u 'Een nieuw project maken' in het opstartscherm.

### Referentie toevoegen aan Aspose.PDF

 Klik met de rechtermuisknop op "Dependencies" in uw projectmap in Solution Explorer. Selecteer "Manage NuGet Packages", zoek naar`Aspose.PDF`, en installeer de nieuwste versie die beschikbaar is. Dit brengt alle tools die u nodig hebt voor het maken en bewerken van PDF's.

### Naamruimten importeren

Voeg bovenaan uw .cs-bestand het volgende toe met behulp van richtlijnen:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Met deze richtlijnen krijgt u naadloos toegang tot de functies van de bibliotheek.

Laten we het proces voor het maken van lokale hyperlinks opsplitsen in eenvoudige stappen.

## Stap 1: Documentinstantie instellen

 Maak een nieuw exemplaar van de`Document` klasse, die het PDF-bestand vertegenwoordigt waarmee u gaat werken.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Stel uw documentmap in
Document doc = new Document(); //Documentinstantie maken
```

 Vervangen`"YOUR_DOCUMENT_DIRECTORY"` met het daadwerkelijke pad op uw systeem waar de PDF wordt opgeslagen.

## Stap 2: Een pagina toevoegen aan het document

Voeg vervolgens een pagina toe aan uw PDF-document.

```csharp
Page page = doc.Pages.Add(); // Een nieuwe pagina toevoegen
```

Met deze regel voegt u een nieuwe pagina toe aan het document. Hierop wordt al uw inhoud geplaatst.

## Stap 3: Maak een tekstfragment

Laten we nu een tekststuk maken dat als klikbare link fungeert.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Maak een tekstfragment
```

 Dit`TextFragment` geeft de tekst weer waarop gebruikers kunnen klikken.

## Stap 4: Lokale hyperlink maken

Maak nu een lokale hyperlink die naar pagina 7 verwijst.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Een lokale hyperlink maken
link.TargetPageNumber = 7; // Stel de doelpagina voor de link in
text.Hyperlink = link; // Stel de hyperlink voor het tekstfragment in
```

 De`LocalHyperlink` Met de klasse kunt u het doelpaginanummer voor de hyperlink opgeven.

## Stap 5: Voeg het tekstfragment toe aan de pagina

Voeg de klikbare tekst toe aan de pagina die u hebt gemaakt.

```csharp
page.Paragraphs.Add(text); // Voeg het tekstfragment toe aan de pagina
```

Met deze regel voegt u uw tekst toe aan de verzameling alinea's van de pagina.

## Stap 6: Maak een ander tekstfragment (optioneel)

Laten we een extra hyperlink toevoegen om terug te navigeren naar pagina 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Een nieuw tekstfragment maken
textBack.IsInNewPage = true; // Geef aan dat het op een nieuwe pagina moet staan
```

## Stap 7: De tweede lokale hyperlink instellen

Maak een andere lokale hyperlink voor pagina 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Een andere lokale hyperlink maken
linkBack.TargetPageNumber = 1; // Doelpagina voor de tweede hyperlink instellen
textBack.Hyperlink = linkBack; // Stel de hyperlink in voor het tweede tekstfragment
```

## Stap 8: Voeg het tweede tekstfragment toe aan de nieuwe pagina

Voeg het tweede tekstfragment toe aan de pagina.

```csharp
Page newPage = doc.Pages.Add(); // Voeg een nieuwe pagina toe voor de tweede link
newPage.Paragraphs.Add(textBack); // Voeg het tekstfragment toe aan de nieuwe pagina
```

## Stap 9: Sla het document op

Sla ten slotte uw document op.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Geef de naam van het uitvoerbestand op
doc.Save(dataDir); // Sla het bijgewerkte document op
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Deze regel combineert uw directorypad met de bestandsnaam en de`Save()` Met deze methode slaat u uw document op.

## Conclusie

Het maken van lokale hyperlinks in PDF-bestanden met Aspose.PDF voor .NET is een praktische functie die de navigatie en gebruikerservaring verbetert. U hebt nu de kennis om uw lezers rechtstreeks naar de informatie te leiden die ze nodig hebben, waardoor uw PDF's interactiever en gebruiksvriendelijker worden.

## Veelgestelde vragen

### Wat is Aspose.PDF voor .NET?
Aspose.PDF voor .NET is een bibliotheek waarmee ontwikkelaars programmatisch PDF-documenten kunnen maken, bewerken en converteren met behulp van het .NET Framework.

### Kan ik hyperlinks naar externe webpagina's maken?
Ja, Aspose.PDF ondersteunt ook het maken van hyperlinks naar externe URL's, naast lokale hyperlinks binnen de PDF.

### Is er een gratis proefversie voor Aspose.PDF?
 Absoluut! Je kunt de gratis proefperiode openen via de[Aspose-website](https://releases.aspose.com/).

### Welke programmeertalen ondersteunt Aspose?
Aspose biedt bibliotheken voor verschillende programmeertalen, waaronder Java, C++en Python, onder andere.

### Hoe krijg ik ondersteuning voor Aspose-producten?
 U kunt ondersteuning zoeken via de[Aspose-forum](https://forum.aspose.com/c/pdf/10).