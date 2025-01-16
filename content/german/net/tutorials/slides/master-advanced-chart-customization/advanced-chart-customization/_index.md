---
title: Erweiterte Diagrammanpassung mit Aspose.Slides für .NET
linktitle: Erweiterte Diagrammanpassung mit Aspose.Slides für .NET
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Schöpfen Sie das volle Potenzial von Aspose.Slides für .NET aus, indem Sie erweiterte Techniken zur Diagrammanpassung beherrschen. Diese Schritt-für-Schritt-Anleitung deckt alles ab, von der grundlegenden Diagrammerstellung bis hin zu komplizierten Details wie Gitternetzlinien, Achsentiteln und benutzerdefinierten Farben.
type: docs
weight: 10
url: /de/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Einführung

Das Erstellen optisch ansprechender und informativer Diagramme ist für eine effektive Datenpräsentation von entscheidender Bedeutung. Aspose.Slides für .NET bietet leistungsstarke Tools zur Diagrammanpassung, mit denen Sie jeden Aspekt Ihrer Diagramme anpassen können. In diesem Tutorial erkunden wir fortgeschrittene Techniken zur Diagrammanpassung mit Aspose.Slides für .NET.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:

1.  Aspose.Slides für .NET-Bibliothek: Laden Sie die Aspose.Slides-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.aspose.com/slides/net/).
2. .NET-Entwicklungsumgebung: Richten Sie eine .NET-Entwicklungsumgebung wie beispielsweise Visual Studio ein.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind von Vorteil, da wir C#-Code schreiben werden.

Lassen Sie uns nun den erweiterten Diagrammanpassungsprozess in klare Schritte unterteilen.

## Schritt 1: Erstellen Sie eine neue Präsentation

Beginnen Sie mit der Erstellung einer neuen Präsentation für Ihr Diagramm.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "Your Document Directory";

// Verzeichnis erstellen, falls es nicht existiert.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Instanziieren der Präsentation
Presentation pres = new Presentation();
```

## Schritt 2: Zugriff auf die erste Folie

Rufen Sie als Nächstes die erste Folie auf, der Sie das Diagramm hinzufügen möchten.

```csharp
// Greifen Sie auf die erste Folie zu
ISlide slide = pres.Slides[0];
```

## Schritt 3: Beispieldiagramm hinzufügen

Fügen wir der Folie nun ein Liniendiagramm mit Markierungen hinzu.

```csharp
// Hinzufügen eines Beispieldiagramms
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Schritt 4: Legen Sie den Diagrammtitel fest

Durch die Festlegung eines Titels für Ihr Diagramm wird der wichtige Kontext bereitgestellt.

```csharp
// Festlegen des Diagrammtitels
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Schritt 5: Hauptrasterlinien anpassen

Zur besseren Lesbarkeit können Sie die Gitternetzlinien der Werteachse verstärken.

```csharp
// Anpassen der Hauptrasterlinien für die Werteachse
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Schritt 6: Kleinere Gitternetzlinien anpassen

Passen Sie auf ähnliche Weise die Nebenrasterlinien für die Werteachse an.

```csharp
// Anpassen der Nebenrasterlinien für die Werteachse
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Schritt 7: Zahlenformat der Werteachse definieren

Sie können die auf der Werteachse angezeigten Zahlen formatieren.

```csharp
// Zahlenformat der Werteachse festlegen
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Schritt 8: Maximal- und Minimalwerte festlegen

Definieren Sie die Maximal- und Minimalwerte für das Diagramm.

```csharp
// Festlegen von Maximal- und Minimalwerten für das Diagramm
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Schritt 9: Texteigenschaften der Werteachse anpassen

Durch die Erweiterung der Texteigenschaften der Werteachse wird die Lesbarkeit verbessert.

```csharp
// Texteigenschaften der Werteachse anpassen
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Schritt 10: Titel der Werteachse hinzufügen

Durch Hinzufügen eines Titels zur Werteachse können Sie verdeutlichen, was die Daten darstellen.

```csharp
// Titel der Werteachse festlegen
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Schritt 11: Hauptrasterlinien für die Kategorieachse anpassen

Lassen Sie uns nun die Hauptrasterlinien für die Kategorieachse verbessern.

```csharp
// Anpassen der Hauptrasterlinien für die Kategorieachse
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Schritt 12: Nebengitterlinien für Kategorieachse anpassen

Passen Sie auf ähnliche Weise die Nebengitterlinien für die Kategorieachse an.

```csharp
// Anpassen der Nebengitterlinien für die Kategorieachse
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Schritt 13: Texteigenschaften der Kategorieachse anpassen

Verbessern Sie den Schriftstil und das Erscheinungsbild der Kategorieachsenbeschriftungen.

```csharp
// Texteigenschaften der Kategorieachse anpassen
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Schritt 14: Titel der Kategorieachse hinzufügen

Bei Bedarf können Sie auch einen Titel für die Kategorieachse hinzufügen.

```csharp
// Kategorieachsentitel festlegen
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Schritt 15: Weitere Anpassungen

Verbessern Sie Ihr Diagramm durch zusätzliche Anpassungen wie Legenden, Wandfarben und Plotbereichseinstellungen.

```csharp
// Zusätzliche Anpassungen (optional)

// Anpassen der Texteigenschaften von Legenden
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Diagrammlegenden ohne überlappendes Diagramm anzeigen
chart.Legend.Overlay = true;

// Festlegen der Rückwandfarbe des Diagramms
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Festlegen der Farbe für den Diagrammboden
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Farbe für Plotbereich festlegen
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Speichern der Präsentation
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Abschluss

In diesem umfassenden Handbuch haben wir erweiterte Diagrammanpassungstechniken mit Aspose.Slides für .NET behandelt. Sie haben gelernt, wie Sie eine Präsentation erstellen, ein Diagramm hinzufügen, sein Erscheinungsbild verfeinern und verschiedene Diagrammelemente wie Gitternetzlinien, Achsenbeschriftungen und Legenden anpassen. 

## Häufig gestellte Fragen

### Welche .NET-Versionen werden von Aspose.Slides für .NET unterstützt?
Aspose.Slides für .NET unterstützt verschiedene .NET-Versionen, darunter .NET Framework und .NET Core. Eine vollständige Liste der unterstützten Versionen finden Sie in der Dokumentation.

### Kann ich Diagramme aus Datenquellen wie Excel-Dateien erstellen?
Ja, mit Aspose.Slides können Sie Diagramme aus externen Datenquellen wie Excel-Tabellen erstellen. Ausführliche Beispiele finden Sie in der Dokumentation.

### Wie kann ich meiner Diagrammreihe benutzerdefinierte Datenbeschriftungen hinzufügen?
 Um benutzerdefinierte Datenbeschriftungen hinzuzufügen, greifen Sie auf die`DataLabels` Eigenschaft der Serie und passen Sie die Beschriftungen nach Bedarf an. Codebeispiele finden Sie in der Dokumentation.

### Ist es möglich, das Diagramm in andere Formate wie PDF oder Bilder zu exportieren?
Auf jeden Fall! Aspose.Slides ermöglicht Ihnen, Ihre Präsentationen mit Diagrammen in verschiedene Formate zu exportieren, darunter PDF und Bildformate.

### Wo finde ich weitere Tutorials und Beispiele für Aspose.Slides für .NET?
 Besuchen Sie die Aspose.Slides[Webseite](https://reference.aspose.com/slides/net/) für ausführliche Tutorials, Codebeispiele und Dokumentation.