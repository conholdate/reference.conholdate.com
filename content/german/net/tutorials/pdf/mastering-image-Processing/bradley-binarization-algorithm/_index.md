---
title: Bradley-Binarisierungsalgorithmus
linktitle: Bradley-Binarisierungsalgorithmus
second_title: Aspose.PDF für .NET API-Referenz
description: Erfahren Sie, wie Sie PDF-Seiten mit dem Bradley-Binarisierungsalgorithmus in Aspose.PDF für .NET in hochwertige binäre TIFF-Bilder konvertieren. Diese Schritt-für-Schritt-Anleitung enthält Codebeispiele.
type: docs
weight: 30
url: /de/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Einführung

In diesem Tutorial führen wir Sie durch den Prozess der Konvertierung einer PDF-Seite in ein TIFF-Bild mithilfe des Bradley-Binarisierungsalgorithmus. Aspose.PDF für .NET vereinfacht diese Aufgabe und ermöglicht Ihnen die mühelose Automatisierung und Optimierung Ihrer Dokumenten-Workflows.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.PDF für .NET: Laden Sie die Bibliothek herunter von[Hier](https://releases.aspose.com/pdf/net/).
- Visual Studio (oder eine beliebige C#-IDE).
- Grundkenntnisse in C#.
-  Eine gültige Lizenz oder ein[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) von Aspose.

## Schritt 1: Richten Sie Ihr Projekt ein

Erstellen Sie zunächst ein neues C#-Projekt in Ihrer IDE und importieren Sie die erforderlichen Namespaces:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Schritt 2: Definieren Sie das Dokumentverzeichnis

Geben Sie den Pfad zum Verzeichnis an, in dem sich Ihr PDF-Dokument befindet, sowie die Ausgabepfade für die TIFF-Bilder:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Pfad zu Ihrer PDF-Datei
```

In diesem Verzeichnis werden sowohl die Quell-PDF- als auch die konvertierten TIFF-Dateien gespeichert.

## Schritt 3: Laden Sie das PDF-Dokument

Öffnen Sie das PDF-Dokument, das Sie konvertieren möchten:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Ersetzen`PageToTIFF.pdf` durch den Namen Ihrer PDF-Datei.

## Schritt 4: Ausgabepfade angeben

Definieren Sie die Ausgabepfade für die generierten TIFF-Dateien:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Schritt 5: Bildauflösung einstellen

Stellen Sie die Auflösung für die TIFF-Bilder ein. Eine höhere DPI ergibt eine bessere Bildqualität:

```csharp
Resolution resolution = new Resolution(300);
```

## Schritt 6: TIFF-Einstellungen konfigurieren

Konfigurieren Sie die Einstellungen für das TIFF-Bild, einschließlich Komprimierung und Farbtiefe:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Durch die Verwendung von 1bpp (1 Bit pro Pixel) wird das Bild für die binäre Ausgabe vorbereitet.

## Schritt 7: Erstellen Sie das TIFF-Gerät

Erstellen Sie ein TIFF-Gerät, das die Konvertierung durchführt:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Schritt 8: Konvertieren Sie die PDF-Seite in TIFF

Konvertieren Sie die erste Seite des PDF in ein TIFF-Bild:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Schritt 9: Den Bradley-Binarisierungsalgorithmus anwenden

Wenden Sie nun den Bradley-Algorithmus an, um das Graustufen-TIFF-Bild in ein Binärbild umzuwandeln:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 Der`BinarizeBradley` Die Methode verwendet zwei Dateiströme (Eingabe und Ausgabe) und einen Schwellenwert. Passen Sie den Schwellenwert nach Bedarf an, um optimale Ergebnisse zu erzielen.

## Schritt 10: Erfolgreiche Konvertierung bestätigen

Bestätigen Sie abschließend, dass die Konvertierung erfolgreich war:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Abschluss

Herzlichen Glückwunsch! Sie haben eine PDF-Seite erfolgreich in ein TIFF-Bild konvertiert und den Bradley-Binarisierungsalgorithmus mit Aspose.PDF für .NET angewendet. Dieser Prozess ist für die Dokumentenarchivierung, OCR und andere professionelle Anwendungen unerlässlich. Mit hochwertiger Auflösung und effizienter Komprimierung sind Ihre Dokumentbilder klar und von handlicher Größe.

## Häufig gestellte Fragen

### Was ist der Bradley-Algorithmus?
Der Bradley-Algorithmus ist eine Binärisierungstechnik, die Graustufenbilder in Binärbilder umwandelt, indem für jedes Pixel auf Grundlage seiner Umgebung ein adaptiver Schwellenwert bestimmt wird.

### Kann ich mit dieser Methode mehrere PDF-Seiten in TIFF konvertieren?
 Ja, Sie können die`Process` Methode, um zur Konvertierung alle Seiten im Dokument zu durchlaufen.

### Was ist die optimale Auflösung für die Konvertierung von PDFs in TIFF?
Für qualitativ hochwertige Bilder wird im Allgemeinen eine Auflösung von 300 DPI empfohlen, Sie können diese jedoch an Ihre spezifischen Anforderungen anpassen.

### Was bedeutet 1bpp in der Farbtiefe?
1bpp (1 Bit pro Pixel) gibt an, dass das Bild schwarzweiß ist und jedes Pixel entweder vollständig schwarz oder vollständig weiß ist.

### Ist der Bradley-Algorithmus für OCR geeignet?
Ja, der Bradley-Algorithmus wird häufig bei der OCR-Vorverarbeitung verwendet, da er den Textkontrast in gescannten Dokumenten verbessert und so die Erkennungsgenauigkeit steigert.