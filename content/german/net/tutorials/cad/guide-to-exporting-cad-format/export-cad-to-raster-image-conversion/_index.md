---
title: Exportieren Sie CAD in die Rasterbildkonvertierung mit Aspose.CAD für .NET
linktitle: CAD-Export zur Rasterbildkonvertierung
second_title: Aspose.CAD .NET - CAD- und BIM-Dateiformat
description: Erfahren Sie, wie Sie CAD-Layouts mit Aspose.CAD für .NET effizient in verschiedene Rasterbildformate konvertieren. Diese umfassende Anleitung führt Sie mit klarem Code durch den Prozess.
type: docs
weight: 10
url: /de/net/tutorials/cad/guide-to-exporting-cad-format/export-cad-to-raster-image-conversion/
---
## Einführung

Möchten Sie CAD-Layouts mühelos mit Aspose.CAD für .NET in Rasterbildformate konvertieren? Diese Schritt-für-Schritt-Anleitung soll Ihnen dabei helfen, den Prozess zu meistern, und enthält prägnante Codeausschnitte für ein reibungsloses Erlebnis. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieses Tutorial bietet wertvolle Einblicke für alle Fähigkeitsstufen.

## Voraussetzungen

Stellen Sie vor dem Start sicher, dass Sie über Folgendes verfügen:

- Aspose.CAD für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von der[Aspose.CAD-Website](https://releases.aspose.com/cad/net/).
-  CAD-Zeichnungsdatei: Halten Sie Ihre CAD-Zeichnungsdatei (z. B.`conic_pyramid.dxf`) bereit zur Konvertierung.

## Erforderliche Namespaces importieren

In Ihrem .NET-Projekt müssen Sie die erforderlichen Namespaces importieren, um Aspose.CAD-Funktionen nutzen zu können. Fügen Sie oben in Ihrem Code Folgendes hinzu:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Schritt 1: Laden Sie Ihre CAD-Zeichnung

Geben Sie zunächst das Verzeichnis an und laden Sie Ihre CAD-Datei in eine Image-Instanz:

```csharp
string MyDir = "Your Document Directory";
string sourceFilePath = MyDir + "conic_pyramid.dxf";

// Laden Sie die CAD-Zeichnung
using (var image = Image.Load(sourceFilePath))
{
    // Fahren Sie mit den nächsten Schritten fort
}
```

## Schritt 2: Rasterisierungsoptionen erstellen

Richten Sie als Nächstes die Rasterungsoptionen ein und definieren Sie die gewünschten Abmessungen für das Ausgabebild:

```csharp
// CadRasterizationOptions initialisieren
var rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 500,
    PageHeight = 500
};
```

## Schritt 3: Ebenen für die Konvertierung festlegen

Wenn Sie bestimmte Ebenen konvertieren möchten, fügen Sie sie Ihren Rasterungsoptionen hinzu:

```csharp
// Geben Sie die zu konvertierende Ebene an
rasterizationOptions.Layers = new [] { "LayerA" };
```

## Schritt 4: JPEG-Exportoptionen einrichten

Erstellen Sie nun Optionen für das Bildformat, in das Sie exportieren möchten (in diesem Fall JPEG):

```csharp
// Erstellen Sie JpegOptions für den Export
var options = new JpegOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Schritt 5: Ins JPEG-Format exportieren

Speichern Sie abschließend das konvertierte Bild:

```csharp
// Definieren Sie den Ausgabedateipfad und speichern Sie das Bild
string outputFilePath = MyDir + "CADLayersToRasterImageFormats_out.jpg";
image.Save(outputFilePath, options);
```

## Zusätzliche Funktion: Alle Ebenen konvertieren

Um alle Ebenen in Ihrer CAD-Zeichnung zu konvertieren, können Sie eine Methode wie diese implementieren:

```csharp
void ConvertAllLayersToRasterImageFormats()
{
    // Durchlaufen Sie die Ebenen und speichern Sie jede als separate JPEG-Datei
    // Ihr Implementierungscode hier
}
```

## Abschluss

Herzlichen Glückwunsch! Sie haben gelernt, wie Sie CAD-Layouts mit Aspose.CAD für .NET effektiv in Rasterbildformate konvertieren. Dieses Handbuch bietet einen unkomplizierten Ansatz für Entwickler, die effiziente CAD-Konvertierungen anstreben.

## Häufig gestellte Fragen

### Kann ich in verschiedene Bildformate exportieren?

 Auf jeden Fall! Tauschen Sie einfach`JpegOptions` mit anderen Formatoptionen, wie`PngOptions` oder`BmpOptions`, je nach Ihren Anforderungen.

### Ist eine Testversion verfügbar?

 Ja, Sie können eine Testversion herunterladen, um die Funktionalität zu erkunden, indem Sie diesem folgen[Link](https://releases.aspose.com/cad/net/).

### Wo finde ich Support für Aspose.CAD?

 Für Community-Support besuchen Sie Aspose.CAD[Forum](https://forum.aspose.com/c/cad/19), oder erwägen Sie den Erwerb einer Lizenz für speziellere Unterstützung.

### Sind befristete Lizenzen möglich?

 Ja, es sind temporäre Lizenzen verfügbar. Sie können eine anfordern.[Hier](https://purchase.conholdate.com/temporary-license/).

### Wo kann ich auf ausführliche Dokumentation zugreifen?

 Besuchen Sie die ausführliche Dokumentation[Hier](https://reference.aspose.com/cad/net/) für weitere Informationen.