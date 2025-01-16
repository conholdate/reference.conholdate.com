---
title: Alternativ för diagrammarkör på datapunkt i Aspose.Slides .NET
linktitle: Alternativ för diagrammarkör på datapunkt i Aspose.Slides .NET
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Lär dig hur du förbättrar dina PowerPoint-diagram med anpassade marköralternativ med Aspose.Slides för .NET. Den här steg-för-steg-guiden täcker förutsättningar, skapande av diagram, formatering av datapunkter och mer.
type: docs
weight: 11
url: /sv/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Introduktion

Att införliva visuella hjälpmedel i presentationer är avgörande för effektiv kommunikation. Aspose.Slides för .NET tillhandahåller robusta verktyg för att skapa och anpassa diagram, vilket gör det möjligt för utvecklare att förbättra sina datapresentationer. En av de utmärkande funktionerna är möjligheten att använda kartmarkeringsalternativ på datapunkter, vilket möjliggör exakt anpassning för proffsiga diagram. Den här artikeln kommer att gå igenom alla steg som behövs för att uppnå detta.

## Förutsättningar

Innan du fortsätter, kontrollera följande:

-  Aspose.Slides för .NET installerat: Ladda ner det från[här](https://releases.aspose.com/slides/net/).
- Grundläggande installation: En presentationsfil, till exempel "Test.pptx," i din arbetskatalog.
- Utvecklingsmiljö: Visual Studio eller motsvarande, konfigurerad för .NET.

## Importera nödvändiga namnområden

Lägg till de nödvändiga namnrymden till ditt projekt för sömlös utveckling:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Steg 1: Skapa ett diagram i din presentation

Börja med att skapa ett standarddiagram på den första bilden av din presentation:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Detta lägger till en`LineWithMarkers` diagram till din bild med specificerade mått.

## Steg 2: Hämta diagramdatakalkylbladsindex

Standarddiagrammets kalkylbladsindex är viktigt för ytterligare anpassning:

```csharp
int defaultWorksheetIndex = 0;
```

## Steg 3: Öppna arbetsboken för diagramdata

För att manipulera diagramdata, hämta den associerade arbetsboken:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Steg 4: Konfigurera diagramserier och lägg till datapunkter

Rensa standardserier och lägg till nya datapunkter för din serie:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Lägg till datapunkter i serien
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Steg 5: Applicera bildfyllningar på datapunktsmarkörer

Anpassade bilder kan göra datamarkörer visuellt tilltalande:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Ställ in anpassade bilder för markörer
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Steg 6: Anpassa markörstorlek

Ändra storleken på markörerna för att öka synligheten:

```csharp
series.Marker.Size = 20;
```

## Steg 7: Spara den uppdaterade presentationen

Spara den anpassade presentationen på önskad plats:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Slutsats

Aspose.Slides för .NET utrustar utvecklare med verktyg för att skapa professionella diagram med rika anpassningsalternativ. Genom att utnyttja alternativen för diagrammarkörer kan du avsevärt förbättra den visuella dragningen och klarheten i dina presentationer. Denna steg-för-steg-guide säkerställer att även komplexa anpassningar är enkla att implementera.

## FAQ's

### Kan jag använda vilket bildformat som helst för marköranpassning?
Ja, Aspose.Slides stöder olika bildformat, inklusive JPEG, PNG och BMP, för marköranpassning.

### Hur ändrar jag diagramtypen efter att jag skapats?
 För att ändra diagramtypen, gå till`chart.Type` egendom och tilldela en annan`ChartType`.

### Är Aspose.Slides för .NET kompatibelt med äldre PowerPoint-versioner?
Ja, den stöder bakåtkompatibilitet med äldre PowerPoint-format, vilket säkerställer mångsidighet.

### Kan jag uppdatera diagramdata dynamiskt?
 Absolut. Använd`IChartDataWorkbook` för att programmatiskt uppdatera sjökortsdata.

### Var kan jag hitta fler resurser?
 Utforska[Aspose.Slides dokumentation](https://reference.aspose.com/slides/net/)eller gå med i[gemenskapsforum](https://forum.aspose.com/) för stöd.