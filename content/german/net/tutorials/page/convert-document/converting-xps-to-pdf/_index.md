---
title: Konvertieren von XPS in PDF mit Aspose.Page für .NET
linktitle: Konvertieren von XPS in PDF
second_title: Aspose.Page .NET API
description: Entdecken Sie, wie Sie XPS-Dokumente (XML Paper Specification) mit der leistungsstarken Aspose.Page-Bibliothek für .NET nahtlos in PDF (Portable Document Format) konvertieren.
type: docs
weight: 11
url: /de/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Einführung

In diesem Tutorial erfahren Sie, wie Sie XPS-Dokumente (XML Paper Specification) mithilfe der vielseitigen Aspose.Page-Bibliothek für .NET in PDF (Portable Document Format) konvertieren. Diese leistungsstarke Bibliothek vereinfacht die Dokumentkonvertierung und bietet verschiedene Anpassungsoptionen, was sie zu einer hervorragenden Wahl für Entwickler macht.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes eingerichtet haben:

-  Aspose.Page für .NET-Bibliothek: Laden Sie die Aspose.Page für .NET-Bibliothek herunter und installieren Sie sie von der[Aspose.Page-Dokumentation](https://reference.aspose.com/page/net/).
  
- Entwicklungsumgebung: Richten Sie mit Visual Studio oder einer anderen kompatiblen IDE eine .NET-Entwicklungsumgebung ein.

- XPS-Dokument: Halten Sie die zu konvertierende XPS-Datei bereit und speichern Sie sie in einem bestimmten Verzeichnis.

## Schritt 1: Erforderliche Namespaces importieren

Beginnen Sie mit dem Importieren des erforderlichen Namespaces, um auf die Aspose.Page-Funktionen zuzugreifen:

```csharp
using Aspose.Page.XPS;
```

## Schritt 2: Dokumentverzeichnis initialisieren

Definieren Sie den Verzeichnispfad, in dem Ihre Dokumente gespeichert sind:

```csharp
string dataDir = "Your Document Directory";
```

 Ersetzen Sie unbedingt`"Your Document Directory"` durch den tatsächlichen Pfad zum Verzeichnis, das Ihr XPS-Dokument enthält.

### Schritt 3: PDF- und XPS-Streams öffnen

Als Nächstes initialisieren Sie die Streams sowohl für die XPS-Eingabedatei als auch für die PDF-Ausgabedatei:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Stellen Sie sicher, dass Sie den richtigen Pfad für Ihre Dateien eingestellt haben.

### Schritt 4: Laden Sie das XPS-Dokument

Laden Sie jetzt Ihr XPS-Dokument mithilfe der Aspose.Page-Bibliothek:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Schritt 5: PDF-Speicheroptionen konfigurieren

Richten Sie die Speicheroptionen für Ihr PDF ein, einschließlich Bildqualität und Komprimierungsparameter:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Festlegen der JPEG-Qualitätsstufe
    ImageCompression = PdfImageCompression.Jpeg, // JPEG-Komprimierung für Bilder verwenden
    TextCompression = PdfTextCompression.Flate, // Flate-Komprimierung für Text anwenden
    PageNumbers = new int[] { 1, 2, 6 } // Geben Sie die einzuschließenden Seitenzahlen an
};
```

Passen Sie diese Parameter gerne Ihren Anforderungen an.

### Schritt 6: Erstellen Sie das PDF-Rendering-Gerät

Erstellen Sie ein Rendering-Gerät für das PDF-Format:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Schritt 7: Speichern Sie das Dokument als PDF

Speichern Sie abschließend das XPS-Dokument mit dem angegebenen Gerät und den angegebenen Optionen als PDF:

```csharp
document.Save(device, options);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben ein XPS-Dokument mit Aspose.Page für .NET erfolgreich in PDF konvertiert. Diese Bibliothek vereinfacht nicht nur die Dokumentkonvertierung, sondern bietet auch umfangreiche Funktionen für die Handhabung verschiedener Formate.

## Häufig gestellte Fragen

### Kann ich mehrere XPS-Dateien in eine einzige PDF konvertieren?

Auf jeden Fall! Sie können mehrere XPS-Dateien durchgehen und sie mit denselben Konvertierungsschritten zu einem einzigen PDF-Dokument zusammenführen.

### Welche anderen Ausgabeformate unterstützt Aspose.Page für .NET?

Zusätzlich zu PDF unterstützt Aspose.Page für .NET eine Reihe von Formaten, darunter TIFF, JPEG und PNG.

### Wie kann ich das Erscheinungsbild der konvertierten PDF-Datei anpassen?

 Sie können die Parameter im`PdfSaveOptions` Objekt, wie etwa JPEG-Qualität und Komprimierungseinstellungen, um das gewünschte Erscheinungsbild zu erreichen.

### Gibt es eine Testversion für Aspose.Page für .NET?

 Ja, Sie können Aspose.Page für .NET mit einer kostenlosen Testversion ausprobieren.[Hier](https://releases.aspose.com/).

### Wo finde ich Community-Support für Aspose.Page für .NET?

Für Community-Diskussionen und Support besuchen Sie die[Aspose.Page-Forum](https://forum.aspose.com/c/page/39).