---
title: Exportieren von Excel-Zellbereichen als Bilder mit Aspose.Cells für .NET
linktitle: Exportieren von Excel-Zellbereichen als Bilder mit Aspose.Cells für .NET
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Erfahren Sie Schritt für Schritt, wie Sie mit Aspose.Cells für .NET bestimmte Zellbereiche in einem Excel-Arbeitsblatt effizient in Bilddateien konvertieren. Diese umfassende Anleitung umfasst Voraussetzungen, Einrichtungsanweisungen und Codebeispiele.
type: docs
weight: 14
url: /de/net/tutorials/cells/mastering-rendering-and-exporting/export-excel-cell-ranges-as-images/
---
## Einführung

Beim Arbeiten mit Excel-Dateien kann das Teilen bestimmter Datenbereiche als Bilder äußerst nützlich sein – sei es für Berichte, Präsentationen oder zum schnellen Teilen. In diesem Handbuch erfahren Sie, wie Sie Zellbereiche mit Aspose.Cells für .NET in Bilder exportieren. Mit Schritt-für-Schritt-Anleitungen sind Sie in der Lage, diesen Vorgang reibungslos durchzuführen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes bereit haben:

1. Visual Studio: Sie müssen Visual Studio auf Ihrem Computer installiert haben.
2.  Aspose.Cells für .NET: Laden Sie die Bibliothek herunter von der[Aspose-Website](https://releases.aspose.com/cells/net/)Sie können eine kostenlose Testversion wählen, um die Funktionen kennenzulernen.
3. Grundlegende C#-Kenntnisse: Wenn Sie mit C# und .NET vertraut sind, können Sie diesem Tutorial leichter folgen.
4. Beispiel-Excel-Datei: Für diese Demonstration verwenden wir eine Datei namens`sampleExportRangeOfCellsInWorksheetToImage.xlsx`, die Sie zu Testzwecken erstellen können.

## Schritt 1: Erforderliche Pakete importieren

Um mit Excel-Dateien und -Bildern in .NET zu arbeiten, müssen Sie die folgenden Namespaces importieren:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Diese Namespaces stellen die erforderlichen Tools zum Verwalten von Arbeitsmappen, Rendern von Bildern und Verwalten von Zeichenoptionen bereit.

## Schritt 2: Verzeichnispfade einrichten

Legen Sie als Nächstes die Quell- und Ausgabeverzeichnispfade fest, in denen sich Ihre Excel-Datei befindet und wo Sie das resultierende Bild speichern möchten.

```csharp
// Definieren Sie die Quell- und Ausgabeverzeichnisse
string sourceDir = "Your Document Directory";
string outputDir = "Your Document Directory";
```

 Ersetzen`"Your Document Directory\\"` durch Ihren tatsächlichen Dateipfad.

## Schritt 3: Erstellen einer Arbeitsmappe aus der Quelldatei

 Erstellen Sie ein`Workbook` Instanz mit Ihrer Excel-Datei:

```csharp
//Laden der Arbeitsmappe
Workbook workbook = new Workbook(sourceDir + "sampleExportRangeOfCellsInWorksheetToImage.xlsx");
```

Diese Zeile öffnet Ihre Excel-Datei zur weiteren Bearbeitung.

## Schritt 4: Zugriff auf das gewünschte Arbeitsblatt

Nachdem Sie die Arbeitsmappe geöffnet haben, müssen Sie auf das spezifische Arbeitsblatt zugreifen, das die Daten enthält, die Sie exportieren möchten.

```csharp
// Greifen Sie auf das erste Arbeitsblatt zu
Worksheet worksheet = workbook.Worksheets[0];
```

Sie können den Index ändern, wenn sich Ihre Daten auf einem anderen Blatt befinden.

## Schritt 5: Definieren Sie den Druckbereich

Geben Sie den Zellbereich an, den Sie in ein Bild umwandeln möchten, indem Sie den Druckbereich festlegen:

```csharp
// Einstellen des Druckbereichs
worksheet.PageSetup.PrintArea = "D8:G16";
```

Passen Sie die Zellbezüge an (`D8:G16`) an Ihre spezifischen Bedürfnisse an.

## Schritt 6: Seitenränder konfigurieren

Um zusätzliche Leerzeichen in Ihrem exportierten Bild zu vermeiden, setzen Sie die Ränder auf Null:

```csharp
// Ränder auf Null setzen
worksheet.PageSetup.LeftMargin = 0;
worksheet.PageSetup.RightMargin = 0;
worksheet.PageSetup.TopMargin = 0;
worksheet.PageSetup.BottomMargin = 0;
```

## Schritt 7: Bildoptionen festlegen

Definieren Sie nun, wie das Bild gerendert werden soll, einschließlich Auflösung und Format:

```csharp
// Bildoptionen erstellen
ImageOrPrintOptions options = new ImageOrPrintOptions
{
    OnePagePerSheet = true,
    ImageType = ImageType.Jpeg,
    HorizontalResolution = 200,
    VerticalResolution = 200
};
```

Hier wird das Bild im JPEG-Format mit 200 DPI sein. Ändern Sie diese Einstellungen nach Bedarf.

## Schritt 8: Rendern Sie das Arbeitsblatt in ein Bild

Es ist Zeit, den angegebenen Bereich in ein Bild umzuwandeln:

```csharp
// Rendern Sie das Arbeitsblatt in ein Bild
SheetRender sr = new SheetRender(worksheet, options);
sr.ToImage(0, outputDir + "outputExportRangeOfCellsInWorksheetToImage.jpg");
```

Dadurch wird das Bild in Ihrem angegebenen Ausgabeverzeichnis gespeichert.

## Schritt 9: Ausführung bestätigen

Um nach dem Export Feedback zu geben, drucken Sie eine Erfolgsmeldung auf die Konsole:

```csharp
Console.WriteLine("ExportRangeOfCellsInWorksheetToImage executed successfully.");
```

## Abschluss

Sie haben erfolgreich gelernt, wie Sie mit Aspose.Cells für .NET einen Zellbereich aus einem Excel-Arbeitsblatt in ein Bild exportieren! Diese Funktion kann besonders praktisch sein, um Daten effizient zu teilen oder visuelle Darstellungen Ihrer Informationen zu erstellen.

## Häufig gestellte Fragen

### Kann ich das Bildformat ändern?

 Ja! Sie können ganz einfach die`ImageType` Eigenschaft in andere Formate wie PNG oder BMP.

### Was ist, wenn ich mehrere Bereiche exportieren möchte?

Sie müssen den Rendervorgang für jeden Bereich wiederholen, den Sie exportieren möchten.

### Gibt es eine Begrenzung für die Größe des Bereichs, den ich exportieren kann?

Aspose.Cells ist für die Verarbeitung großer Bereiche ausgelegt, die Leistung kann jedoch variieren. Es ist eine gute Idee, innerhalb angemessener Grenzen zu testen.

### Kann ich diesen Prozess automatisieren?

Auf jeden Fall! Sie können diese Funktionalität zur Automatisierung in größere Anwendungen oder Skripte integrieren.

### Wo kann ich zusätzliche Unterstützung erhalten?

 Weitere Hilfe erhalten Sie im[Aspose Support Forum](https://forum.aspose.com/c/cells/9).