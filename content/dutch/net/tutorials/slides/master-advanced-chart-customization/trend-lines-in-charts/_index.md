---
title: Trendlijnen in grafieken met Aspose.Slides voor .NET
linktitle: Trendlijnen in grafieken met Aspose.Slides voor .NET
second_title: Aspose.Slides .NET PowerPoint-verwerkings-API
description: Leer hoe u trendlijnen in grafieken kunt toevoegen en aanpassen met Aspose.Slides voor .NET. Deze uitgebreide gids behandelt exponentiële, lineaire, logaritmische, polynomiale en voortschrijdende gemiddelde trendlijnen om uw datavisualisatie te verbeteren.
type: docs
weight: 12
url: /nl/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Invoering  

Trendlijnen toevoegen aan grafieken is een belangrijke techniek voor het analyseren van datatrends en het voorspellen van toekomstige waarden. Met Aspose.Slides voor .NET kunt u naadloos trendlijnen toevoegen en aanpassen aan uw presentatiegrafieken, waardoor uw datavisualisatie wordt verbeterd. Deze gids biedt een gedetailleerde walkthrough voor het toevoegen van trendlijnen aan verschillende grafiektypen in een PowerPoint-presentatie met behulp van Aspose.Slides voor .NET.  

## Vereisten  

Voordat we met de implementatie beginnen, moet u ervoor zorgen dat u de volgende instellingen hebt:  

1.  Aspose.Slides voor .NET: Download en installeer de bibliotheek van de[downloadpagina](https://releases.aspose.com/slides/net/).  
2. Ontwikkelomgeving: Gebruik een IDE zoals Visual Studio voor codering.  
3. Basiskennis van C#: Om deze tutorial te kunnen volgen, is kennis van C#-programmering vereist.  

## Vereiste naamruimten importeren  

Om te beginnen importeert u de essentiële naamruimten in uw project:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Stap 1: De presentatie instellen  

Initialiseer eerst een lege presentatie. Deze zal dienen als container voor uw grafiek.  

```csharp
string dataDir = "Your/Documents/Directory";

// Zorg ervoor dat de directory bestaat
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Een nieuwe presentatie maken
Presentation presentation = new Presentation();
```

## Stap 2: Een grafiek toevoegen aan een dia  

Voeg nu een dia toe en een geclusterd kolomdiagram om uw gegevens te visualiseren.  

```csharp
// Een lege dia toevoegen
ISlide slide = presentation.Slides[0];

// Voeg een geclusterde kolomgrafiek toe
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Stap 3: Grafiekgegevens invullen  

Vul de grafiek met voorbeeldgegevens.  

```csharp
// Toegang tot de standaard grafiekgegevenswerkmap
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Standaardcategorieën en seriewaarden bijwerken
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Stap 4: Trendlijnen toevoegen  

### Exponentiële trendlijn  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Lineaire trendlijn  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Logaritmische trendlijn  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Trendlijn van het voortschrijdende gemiddelde  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Polynomiale trendlijn  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Kracht trendlijn  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Stap 5: De presentatie opslaan  

Sla ten slotte de presentatie op met alle trendlijnen die u aan uw grafiek hebt toegevoegd.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Conclusie  

Met Aspose.Slides voor .NET wordt het toevoegen van trendlijnen aan uw grafieken een eenvoudige taak. Met deze functie kunt u datatrends effectief presenteren en professionele accenten toevoegen aan uw presentaties. Volg de bovenstaande stappen om verschillende trendlijntypen op te nemen en uw datavisualisatie te verbeteren.  

## Veelgestelde vragen  

### Kan ik het uiterlijk van trendlijnen aanpassen?  
 Ja, u kunt de kleur, dikte en stijl van trendlijnen aanpassen met behulp van de`Format.Line` eigendom.  

### Wordt er ondersteuning geboden voor andere grafiektypen?  
Ja, Aspose.Slides voor .NET ondersteunt verschillende grafiektypen, waaronder staaf-, cirkel- en lijndiagrammen.  

### Hoe geef ik vergelijkingen en R-kwadraatwaarden weer?  
 Inschakelen`DisplayEquation` En`DisplayRSquaredValue` Eigenschappen voor een trendlijn om deze waarden in de grafiek weer te geven.  

### Kan ik Aspose.Slides voor .NET met andere talen gebruiken?  
Ja, de bibliotheek is compatibel met alle door .NET ondersteunde talen, inclusief VB.NET en F#.  

### Waar kan ik meer documentatie vinden?  
 Bezoek de[Aspose.Slides voor .NET-documentatie](https://reference.aspose.com/slides/net/) voor meer informatie.