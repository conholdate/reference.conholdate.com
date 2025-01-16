---
title: Diagrammmarkierungsoptionen für Datenpunkte in Aspose.Slides .NET
linktitle: Diagrammmarkierungsoptionen für Datenpunkte in Aspose.Slides .NET
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Erfahren Sie, wie Sie Ihre PowerPoint-Diagramme mit benutzerdefinierten Markierungsoptionen mithilfe von Aspose.Slides für .NET verbessern können. Diese Schritt-für-Schritt-Anleitung behandelt Voraussetzungen, Diagrammerstellung, Datenpunktformatierung und mehr.
type: docs
weight: 11
url: /de/net/tutorials/slides/master-advanced-chart-customization/chart-marker-options/
---
## Einführung

Die Einbindung visueller Hilfsmittel in Präsentationen ist für eine wirkungsvolle Kommunikation unerlässlich. Aspose.Slides für .NET bietet robuste Tools zum Erstellen und Anpassen von Diagrammen, mit denen Entwickler ihre Datenpräsentationen verbessern können. Eine der herausragenden Funktionen ist die Möglichkeit, Diagrammmarkierungsoptionen für Datenpunkte zu verwenden, was eine präzise Anpassung für professionell aussehende Diagramme ermöglicht. Dieser Artikel führt Sie durch jeden Schritt, der dazu erforderlich ist.

## Voraussetzungen

Bevor Sie fortfahren, stellen Sie Folgendes sicher:

-  Aspose.Slides für .NET Installiert: Laden Sie es herunter von[Hier](https://releases.aspose.com/slides/net/).
- Grundlegende Einrichtung: Eine Präsentationsdatei, z. B. „Test.pptx“, in Ihrem Arbeitsverzeichnis.
- Entwicklungsumgebung: Visual Studio oder gleichwertig, konfiguriert für .NET.

## Importieren erforderlicher Namespaces

Fügen Sie Ihrem Projekt für eine reibungslose Entwicklung die erforderlichen Namespaces hinzu:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Schritt 1: Erstellen Sie ein Diagramm in Ihrer Präsentation

Beginnen Sie mit der Erstellung eines Standarddiagramms auf der ersten Folie Ihrer Präsentation:

```csharp
string dataDir = "Your Document Directory";
Presentation pres = new Presentation(dataDir + "Test.pptx");
ISlide slide = pres.Slides[0];

IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 600, 400);
```

 Dies fügt eine`LineWithMarkers` Fügen Sie Ihrer Folie ein Diagramm mit den angegebenen Abmessungen hinzu.

## Schritt 2: Abrufen des Arbeitsblattindexes für Diagrammdaten

Der Standardarbeitsblattindex für Diagrammdaten ist für die weitere Anpassung wichtig:

```csharp
int defaultWorksheetIndex = 0;
```

## Schritt 3: Zugriff auf die Arbeitsmappe mit Diagrammdaten

Um Diagrammdaten zu bearbeiten, rufen Sie die zugehörige Arbeitsmappe ab:

```csharp
IChartDataWorkbook fact = chart.ChartData.ChartDataWorkbook;
```

## Schritt 4: Diagrammserien konfigurieren und Datenpunkte hinzufügen

Löschen Sie die Standardreihen und fügen Sie Ihrer Reihe neue Datenpunkte hinzu:

```csharp
chart.ChartData.Series.Clear();
chart.ChartData.Series.Add(fact.GetCell(defaultWorksheetIndex, 1, 1, "Series 1"), chart.Type);

// Datenpunkte zur Reihe hinzufügen
IChartSeries series = chart.ChartData.Series[0];
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 1, 2, 4.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 2, 2, 2.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 3, 2, 3.5));
series.DataPoints.AddDataPointForLineSeries(fact.GetCell(defaultWorksheetIndex, 4, 2, 4.0));
```

## Schritt 5: Bildfüllungen auf Datenpunktmarkierungen anwenden

Benutzerdefinierte Bilder können Datenmarkierungen optisch ansprechend gestalten:

```csharp
System.Drawing.Image img1 = (System.Drawing.Image)new Bitmap(dataDir + "aspose-logo.jpg");
IPPImage imgx1 = pres.Images.AddImage(img1);

System.Drawing.Image img2 = (System.Drawing.Image)new Bitmap(dataDir + "flower.jpg");
IPPImage imgx2 = pres.Images.AddImage(img2);

// Benutzerdefinierte Bilder für Markierungen festlegen
series.DataPoints[0].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[0].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx1;

series.DataPoints[1].Marker.Format.Fill.FillType = FillType.Picture;
series.DataPoints[1].Marker.Format.Fill.PictureFillFormat.Picture.Image = imgx2;
```

## Schritt 6: Markergröße anpassen

Ändern Sie die Größe der Markierungen, um die Sichtbarkeit zu verbessern:

```csharp
series.Marker.Size = 20;
```

## Schritt 7: Speichern Sie die aktualisierte Präsentation

Speichern Sie die angepasste Präsentation am gewünschten Ort:

```csharp
pres.Save(dataDir + "CustomizedChart.pptx", SaveFormat.Pptx);
```

## Abschluss

Aspose.Slides für .NET stattet Entwickler mit Tools zum Erstellen professioneller Diagramme mit umfangreichen Anpassungsoptionen aus. Durch die Nutzung von Diagrammmarkierungsoptionen können Sie die visuelle Attraktivität und Klarheit Ihrer Präsentationen erheblich verbessern. Diese Schritt-für-Schritt-Anleitung stellt sicher, dass selbst komplexe Anpassungen einfach umzusetzen sind.

## Häufig gestellte Fragen

### Kann ich zur Markeranpassung jedes beliebige Bildformat verwenden?
Ja, Aspose.Slides unterstützt verschiedene Bildformate, darunter JPEG, PNG und BMP, zur Markeranpassung.

### Wie ändere ich den Diagrammtyp nach der Erstellung?
 Um den Diagrammtyp zu ändern, rufen Sie das`chart.Type` und weisen Sie eine andere`ChartType`.

### Ist Aspose.Slides für .NET mit älteren PowerPoint-Versionen kompatibel?
Ja, es unterstützt die Abwärtskompatibilität mit älteren PowerPoint-Formaten und gewährleistet so Vielseitigkeit.

### Kann ich Diagrammdaten dynamisch aktualisieren?
 Auf jeden Fall. Nutzen Sie die`IChartDataWorkbook` um Diagrammdaten programmgesteuert zu aktualisieren.

### Wo finde ich weitere Ressourcen?
 Entdecken Sie die[Aspose.Slides-Dokumentation](https://reference.aspose.com/slides/net/)oder treten Sie dem[Community-Foren](https://forum.aspose.com/) für die Unterstützung.