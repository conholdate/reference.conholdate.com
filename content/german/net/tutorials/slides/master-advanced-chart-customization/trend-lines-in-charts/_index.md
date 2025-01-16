---
title: Trendlinien in Diagrammen mit Aspose.Slides für .NET
linktitle: Trendlinien in Diagrammen mit Aspose.Slides für .NET
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Slides für .NET Trendlinien in Diagrammen hinzufügen und anpassen. Dieser umfassende Leitfaden behandelt exponentielle, lineare, logarithmische, polynomische und gleitende Durchschnittstrendlinien, um Ihre Datenvisualisierung zu verbessern.
type: docs
weight: 12
url: /de/net/tutorials/slides/master-advanced-chart-customization/trend-lines-in-charts/
---
## Einführung  

Das Hinzufügen von Trendlinien zu Diagrammen ist eine wichtige Technik zur Analyse von Datentrends und zur Prognose zukünftiger Werte. Mit Aspose.Slides für .NET können Sie Ihren Präsentationsdiagrammen nahtlos Trendlinien hinzufügen und anpassen und so Ihre Datenvisualisierung verbessern. Dieses Handbuch bietet eine detaillierte Anleitung zum Hinzufügen von Trendlinien zu verschiedenen Diagrammtypen in einer PowerPoint-Präsentation mit Aspose.Slides für .NET.  

## Voraussetzungen  

Bevor wir mit der Implementierung beginnen, stellen Sie sicher, dass Sie über die folgende Konfiguration verfügen:  

1.  Aspose.Slides für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von der[Download-Seite](https://releases.aspose.com/slides/net/).  
2. Entwicklungsumgebung: Verwenden Sie zum Codieren eine IDE wie Visual Studio.  
3. Grundlegende C#-Kenntnisse: Um diesem Tutorial folgen zu können, sind Kenntnisse in der C#-Programmierung erforderlich.  

## Importieren erforderlicher Namespaces  

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:  

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Schritt 1: Einrichten der Präsentation  

Initialisieren Sie zunächst eine leere Präsentation. Diese dient als Container für Ihr Diagramm.  

```csharp
string dataDir = "Your/Documents/Directory";

// Stellen Sie sicher, dass das Verzeichnis vorhanden ist
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Erstellen einer neuen Präsentation
Presentation presentation = new Presentation();
```

## Schritt 2: Hinzufügen eines Diagramms zu einer Folie  

Fügen Sie jetzt eine Folie hinzu und fügen Sie ein gruppiertes Säulendiagramm ein, um Ihre Daten zu visualisieren.  

```csharp
// Hinzufügen einer leeren Folie
ISlide slide = presentation.Slides[0];

// Hinzufügen eines gruppierten Säulendiagramms
IChart chart = slide.Shapes.AddChart(ChartType.ClusteredColumn, 50, 50, 500, 400);
```

## Schritt 3: Diagrammdaten füllen  

Füllen Sie das Diagramm mit Beispieldaten.  

```csharp
// Auf die standardmäßige Diagrammdatenarbeitsmappe zugreifen
IChartDataWorkbook workbook = chart.ChartData.ChartDataWorkbook;

// Aktualisieren der Standardkategorien und Serienwerte
workbook.Clear(0);
workbook.GetCell(0, 0, 1).Value = "Category 1";
workbook.GetCell(0, 0, 2).Value = "Category 2";

chart.ChartData.Series[0].DataPoints[0].Value.Data = 4.5;
chart.ChartData.Series[0].DataPoints[1].Value.Data = 2.8;
```

## Schritt 4: Trendlinien hinzufügen  

### Exponentielle Trendlinie  

```csharp
ITrendline expTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Exponential);
expTrendLine.DisplayEquation = true;
expTrendLine.DisplayRSquaredValue = true;
```

### Lineare Trendlinie  

```csharp
ITrendline linTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Linear);
linTrendLine.Format.Line.FillFormat.FillType = FillType.Solid;
linTrendLine.Format.Line.FillFormat.SolidFillColor.Color = Color.Blue;
```

### Logarithmische Trendlinie  

```csharp
ITrendline logTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Logarithmic);
logTrendLine.AddTextFrameForOverriding("Logarithmic Trend");
```

### Trendlinie des gleitenden Durchschnitts  

```csharp
ITrendline movAvgTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.MovingAverage);
movAvgTrendLine.Period = 3;
movAvgTrendLine.TrendlineName = "3-Point Moving Average";
```

### Polynomische Trendlinie  

```csharp
ITrendline polyTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Polynomial);
polyTrendLine.Order = 2;
polyTrendLine.Forward = 1;
```

### Power-Trendlinie  

```csharp
ITrendline powerTrendLine = chart.ChartData.Series[0].TrendLines.Add(TrendlineType.Power);
powerTrendLine.DisplayEquation = true;
powerTrendLine.Backward = 1;
```

## Schritt 5: Speichern der Präsentation  

Speichern Sie abschließend die Präsentation mit allen zu Ihrem Diagramm hinzugefügten Trendlinien.  

```csharp
presentation.Save(dataDir + "TrendLinesPresentation.pptx", SaveFormat.Pptx);
```

## Abschluss  

Mit Aspose.Slides für .NET wird das Hinzufügen von Trendlinien zu Ihren Diagrammen zu einer einfachen Aufgabe. Mit dieser Funktion können Sie Datentrends effektiv darstellen und Ihren Präsentationen einen professionellen Touch verleihen. Befolgen Sie die obigen Schritte, um verschiedene Trendlinientypen einzubinden und Ihre Datenvisualisierung zu verbessern.  

## Häufig gestellte Fragen  

### Kann ich das Erscheinungsbild von Trendlinien anpassen?  
 Ja, Sie können die Farbe, Dicke und den Stil von Trendlinien anpassen, indem Sie`Format.Line` Eigentum.  

### Gibt es Unterstützung für andere Diagrammtypen?  
Ja, Aspose.Slides für .NET unterstützt verschiedene Diagrammtypen, darunter Balken-, Kreis- und Liniendiagramme.  

### Wie zeige ich Gleichungen und R-Quadrat-Werte an?  
 Aktivieren`DisplayEquation` Und`DisplayRSquaredValue` Eigenschaften für eine Trendlinie, um diese Werte im Diagramm anzuzeigen.  

### Kann ich Aspose.Slides für .NET mit anderen Sprachen verwenden?  
Ja, die Bibliothek ist mit jeder von .NET unterstützten Sprache kompatibel, einschließlich VB.NET und F#.  

### Wo finde ich weitere Unterlagen?  
 Besuchen Sie die[Aspose.Slides für .NET-Dokumentation](https://reference.aspose.com/slides/net/) für weitere Informationen.