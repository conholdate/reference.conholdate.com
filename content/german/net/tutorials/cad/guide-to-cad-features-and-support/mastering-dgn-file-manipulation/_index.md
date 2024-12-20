---
title: Beherrschung der DGN-Dateibearbeitung mit Aspose.CAD in .NET
linktitle: Beherrschen der DGN-Dateibearbeitung
second_title: Aspose.CAD .NET - CAD- und BIM-Dateiformat
description: Erfahren Sie, wie Sie DGN-Dateien laden, ihre Elemente durchlaufen, sowohl 2D- als auch 3D-Objekte verwalten und sie als Rasterbilder exportieren – und dabei die leistungsstarken Funktionen der Aspose.CAD-Bibliothek nutzen.
type: docs
weight: 18
url: /de/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Einführung

Sind Sie ein .NET-Entwickler, der DGN-Dateien in seine Anwendungen integrieren möchte? Aspose.CAD für .NET bietet eine leistungsstarke Bibliothek, die speziell für die Arbeit mit DGN-Dateiformaten entwickelt wurde. In diesem Tutorial erfahren Sie, wie Sie DGN-Dateien, einschließlich unterstützter Elemente, effizient handhaben und in Ihren .NET-Projekten bearbeiten können.

## Voraussetzungen

Stellen Sie vor dem Beginn sicher, dass Sie über die folgende Konfiguration verfügen:

- Grundkenntnisse der .NET-Programmierung: Kenntnisse in C# oder VB.NET sind von Vorteil.
- Visual Studio: Wird zur Projektentwicklung auf Ihrem Computer installiert.
-  Aspose.CAD für .NET-Bibliothek: Laden Sie es herunter von[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Schritt 1: Erforderliche Namespaces importieren

Um die Funktionen von Aspose.CAD zu nutzen, importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Schritt 2: Laden Sie Ihre DGN-Datei

 Laden Sie zunächst eine vorhandene DGN-Datei in Ihre Anwendung. Dies geschieht durch die Instanziierung eines`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Fahren Sie hier mit Ihrer Logik fort
}
```

## Schritt 3: Durch DGN-Elemente iterieren

Sobald die DGN-Datei geladen ist, können Sie ihre Elemente durchlaufen. Aspose.CAD bietet eine Vielzahl von DGN-Elementtypen für Ihre Bearbeitung.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Verarbeiten Sie jedes Element
}
```

## Schritt 4: 2D- und 3D-Objekte handhaben

Man unterscheidet zwischen 2D- und 3D-DGN-Elementen. Im Folgenden erfahren Sie, wie Sie diese effizient handhaben:

### 2D-Objekte handhaben

Sie können zuvor unterstützte 2D-Objekte mit einem Switch-Case-Block verwalten.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Fügen Sie hier Ihre Verarbeitungslogik hinzu
        break;
}
```

### 3D-Objekte handhaben

Behandeln Sie 3D-Objekte analog dazu wie folgt:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Fügen Sie hier Ihre Verarbeitungslogik hinzu
        break;
}
```

## Schritt 5: Exportieren der DGN-Datei

Nach der Bearbeitung der DGN-Elemente möchten Sie die Datei möglicherweise als Rasterbild exportieren. Dies lässt sich problemlos mit Aspose.CAD erreichen.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Definieren Sie Ihren Ausgabepfad
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Abschluss

In diesem Tutorial haben wir gelernt, wie Sie mit Aspose.CAD für .NET DGN-Dateien effektiv verwalten. Indem Sie die beschriebenen Schritte befolgen, können Sie mühelos sowohl 2D- als auch 3D-DGN-Elemente verarbeiten und als Rasterbilder exportieren. Diese leistungsstarke Bibliothek ermöglicht die nahtlose Integration der DGN-Verarbeitung in Ihre .NET-Anwendungen und erweitert so Ihre Projektfunktionen.

## Häufig gestellte Fragen

### Wo finde ich die Dokumentation für Aspose.CAD für .NET?

 Die ausführliche Dokumentation ist verfügbar[Hier](https://reference.aspose.com/cad/net/).

### Wie lade ich Aspose.CAD für .NET herunter?

 Sie können die neueste Version der Bibliothek herunterladen[Hier](https://releases.aspose.com/cad/net/).

### Gibt es eine kostenlose Testversion für Aspose.CAD für .NET?

 Ja, eine kostenlose Testversion ist verfügbar[Hier](https://releases.aspose.com/).

### Wie kann ich temporäre Lizenzen für Aspose.CAD für .NET erhalten?

 Sie können temporäre Lizenzen anfordern[Hier](https://purchase.conholdate.com/temporary-license/).

### Brauchen Sie Hilfe oder haben Sie Fragen?

Wenn Sie Unterstützung benötigen oder Fragen stellen möchten, besuchen Sie die Aspose.CAD-Community[Support-Forum](https://forum.aspose.com/c/cad/19).