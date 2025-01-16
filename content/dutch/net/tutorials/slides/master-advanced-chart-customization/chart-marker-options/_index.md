---
title: Grafiekmarkeringsopties op gegevenspunt in Aspose.Slides .NET
linktitle: Grafiekmarkeringsopties op gegevenspunt in Aspose.Slides .NET
second_title: Aspose.Slides .NET PowerPoint-verwerkings-API
description: Leer hoe u uw PowerPoint-grafieken kunt verbeteren met aangepaste markeropties met Aspose.Slides voor .NET. Deze stapsgewijze handleiding behandelt vereisten, het maken van grafieken, het opmaken van gegevenspunten en meer.
type: docs
weight: 11
url: /nl/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Invoering

Het opnemen van visuele hulpmiddelen in presentaties is essentieel voor impactvolle communicatie. Aspose.Slides voor .NET biedt robuuste tools voor het maken en aanpassen van grafieken, waardoor ontwikkelaars hun datapresentaties kunnen verbeteren. Een van de opvallende functies is de mogelijkheid om grafiekmarkeringsopties op datapunten te gebruiken, wat nauwkeurige aanpassing voor professioneel ogende grafieken mogelijk maakt. Dit artikel leidt u door elke stap die nodig is om dit te bereiken.

## Vereisten

Controleer het volgende voordat u verdergaat:

-  Aspose.Slides voor .NET Geïnstalleerd: Download het van[hier](https://releases.aspose.com/slides/net/).
- Basisinstellingen: Een presentatiebestand, bijvoorbeeld 'Test.pptx', in uw werkmap.
- Ontwikkelomgeving: Visual Studio of gelijkwaardig, geconfigureerd voor .NET.

## Vereiste naamruimten importeren

Voeg de benodigde naamruimten toe aan uw project voor een naadloze ontwikkeling:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Stap 1: Maak een grafiek in uw presentatie

Begin met het maken van een standaardgrafiek op de eerste dia van uw presentatie:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Dit voegt een`LineWithMarkers` grafiek aan uw dia toevoegen met de opgegeven afmetingen.

## Stap 2: Haal de index van het grafiekgegevensblad op

De standaardindex van het grafiekgegevensblad is essentieel voor verdere aanpassing:

```csharp
int defaultWorksheetIndex = 0;
```

## Stap 3: Toegang tot de grafiekgegevenswerkmap

Om grafiekgegevens te bewerken, haalt u de bijbehorende werkmap op:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Stap 4: Grafiekreeksen configureren en datapunten toevoegen

Wis de standaardreeks en voeg nieuwe datapunten toe aan uw reeks:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Voeg datapunten toe aan de reeks
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Stap 5: Pas afbeeldingvullingen toe op gegevenspuntmarkeringen

Aangepaste afbeeldingen kunnen gegevensmarkeringen visueel aantrekkelijk maken:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Aangepaste afbeeldingen voor markeringen instellen
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Stap 6: Pas de markergrootte aan

Wijzig de grootte van de markeringen om de zichtbaarheid te verbeteren:

```csharp
series.Marker.Size = 20;
```

## Stap 7: Sla de bijgewerkte presentatie op

Sla de aangepaste presentatie op de gewenste locatie op:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Conclusie

Aspose.Slides voor .NET voorziet ontwikkelaars van hulpmiddelen om professionele grafieken te maken met uitgebreide aanpassingsopties. Door gebruik te maken van grafiekmarkeringsopties, kunt u de visuele aantrekkingskracht en helderheid van uw presentaties aanzienlijk verbeteren. Deze stapsgewijze handleiding zorgt ervoor dat zelfs complexe aanpassingen eenvoudig te implementeren zijn.

## Veelgestelde vragen

### Kan ik elk afbeeldingsformaat gebruiken voor het aanpassen van markers?
Ja, Aspose.Slides ondersteunt verschillende afbeeldingsformaten, waaronder JPEG, PNG en BMP, voor het aanpassen van markers.

### Hoe kan ik het grafiektype wijzigen nadat ik het heb gemaakt?
 Om het grafiektype te wijzigen, gaat u naar de`chart.Type` eigendom en wijs een andere toe`ChartType`.

### Is Aspose.Slides voor .NET compatibel met oudere PowerPoint-versies?
Ja, het ondersteunt achterwaartse compatibiliteit met oudere PowerPoint-formaten, wat veelzijdigheid garandeert.

### Kan ik grafiekgegevens dynamisch bijwerken?
 Absoluut. Gebruik de`IChartDataWorkbook` om grafiekgegevens programmatisch bij te werken.

### Waar kan ik meer informatie vinden?
 Ontdek de[Aspose.Slides-documentatie](https://reference.aspose.com/slides/net/)of sluit je aan bij de[gemeenschapsforums](https://forum.aspose.com/) voor ondersteuning.