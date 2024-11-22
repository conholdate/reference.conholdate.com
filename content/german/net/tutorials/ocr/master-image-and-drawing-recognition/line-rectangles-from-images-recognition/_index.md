---
title: Extrahieren von Linienrechtecken aus der Bilderkennung
linktitle: Extrahieren von Linienrechtecken aus der Bilderkennung
second_title: Aspose.OCR .NET API
description: Erfahren Sie, wie Sie mit Aspose.OCR die optische Zeichenerkennung (OCR) in Ihren .NET-Anwendungen implementieren. Diese umfassende Anleitung führt Sie durch den Prozess des Extrahierens von Rechtecken für erkannte Linien.
type: docs
weight: 10
url: /de/net/tutorials/ocr/master-image-and-drawing-recognition/line-rectangles-from-images-recognition/
---
## Einführung

Willkommen in der Welt von Aspose.OCR für .NET, einem beeindruckenden Tool zur Integration der optischen Zeichenerkennung (OCR) in Ihre .NET-Anwendungen. Egal, ob Sie ein erfahrener Entwickler oder ein neugieriger Neuling sind, dieser Leitfaden führt Sie durch die Schritte zum Erhalten von Rechtecken, die Zeilen aus erkanntem Text in Bildern darstellen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Folgendes vorhanden ist:

- Grundkenntnisse in C#- und .NET-Entwicklung.
- Eine integrierte Entwicklungsumgebung (IDE) wie Visual Studio.
-  Die Aspose.OCR für .NET-Bibliothek ist installiert. Sie können sie herunterladen[Hier](https://releases.aspose.com/ocr/net/).
- Ein Beispielbild mit Text zur Erkennung.

## Erforderliche Namespaces

Zu Beginn müssen Sie Ihrem Projekt die erforderlichen Namespaces hinzufügen. Fügen Sie diese Zeilen oben in Ihre C#-Datei ein:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
```

Befolgen Sie diese Schritte, um Rechtecke für Linien in einem OCR-Bild abzurufen.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Geben Sie das Verzeichnis an, in dem sich Ihre Bilddatei befindet:

```csharp
// Definieren Sie den Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "Your Document Directory";
```

 Ersetzen Sie unbedingt`"Your Document Directory"` mit dem tatsächlichen Pfad.

## Schritt 2: Aspose.OCR initialisieren

 Erstellen Sie eine Instanz des`AsposeOcr` Klasse, um auf ihre Funktionen zuzugreifen:

```csharp
// Initialisieren Sie die Aspose.OCR-API
AsposeOcr api = new AsposeOcr();
```

## Schritt 3: Bildpfad angeben

Geben Sie den vollständigen Pfad zur Bilddatei an, die Sie verarbeiten möchten:

```csharp
// Geben Sie den vollständigen Pfad zum Bild an
string fullPath = dataDir + "sample.png";
```

## Schritt 4: Bild erkennen und Rechtecke für Linien erhalten

 Jetzt können Sie die`GetRectangles` Methode zum Extrahieren von Rechtecken aus erkannten Textzeilen:

```csharp
// Rechtecke für Linien im angegebenen Bild abrufen
List<Rectangle> lines = api.GetRectangles(fullPath, AreasType.LINES, false);
```

## Schritt 5: Ergebnisse ausgeben

Drucken Sie abschließend die Koordinaten jedes erkannten Linienrechtecks auf der Konsole aus:

```csharp
// Anzeige der Koordinaten der erkannten Rechtecke
Console.WriteLine("Areas coordinates:");
lines.ForEach(a => Console.WriteLine($"x:{a.X} y:{a.Y} width:{a.Width} height:{a.Height}"));
```

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.OCR für .NET erfolgreich Rechtecke für Linien in einem OCR-Bild abgerufen. Diese Technologie eröffnet zahlreiche Möglichkeiten zur Textextraktion und -verarbeitung in Ihren Anwendungen.

## Häufig gestellte Fragen

### Kann ich Aspose.OCR für .NET mit jedem Bildtyp verwenden?

Ja, Aspose.OCR unterstützt verschiedene Bildformate und bietet Flexibilität für Ihre OCR-Anwendungen.

### Wie hoch ist die Genauigkeit der OCR-Erkennung?

Aspose.OCR verwendet fortschrittliche Algorithmen, um eine hohe Genauigkeit bei der Texterkennung zu erreichen, die für verschiedene Szenarien geeignet ist.

### Ist eine Testversion verfügbar?

 Ja, Sie können die Funktionen von Aspose.OCR für .NET erkunden, indem Sie die[Kostenlose Testversion](https://releases.aspose.com/).

### Wo finde ich eine ausführliche Dokumentation?

 Ausführliche Dokumentation finden Sie[Hier](https://reference.aspose.com/ocr/net/), bietet ausführliche Informationen und Richtlinien.

### Benötigen Sie weitere Hilfe oder haben Sie Fragen?

 Diskutieren Sie mit im[Aspose.OCR-Forum](https://forum.aspose.com/c/ocr/16) für die Unterstützung der Community.