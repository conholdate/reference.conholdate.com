---
title: Extrahieren Sie Audio aus Hyperlinks in PowerPoint mit Aspose.Slides
linktitle: Audio aus Hyperlinks extrahieren
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Slides für .NET Audio aus Hyperlinks in PowerPoint-Präsentationen extrahieren. Diese Schritt-für-Schritt-Anleitung enthält klare Anweisungen.
type: docs
weight: 12
url: /de/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Einführung

In Multimediapräsentationen steigert Audio die Wirkung Ihrer Folien erheblich. Wenn Sie schon einmal eine PowerPoint-Präsentation mit Audio-Hyperlinks gesehen haben und sich gefragt haben, wie Sie dieses Audio für andere Zwecke extrahieren können, sind Sie hier richtig. Diese Anleitung führt Sie durch den Prozess des Extrahierens von Audio aus Hyperlinks in einer PowerPoint-Präsentation mithilfe der Aspose.Slides für .NET-Bibliothek.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

### Aspose.Slides für .NET-Bibliothek

 Stellen Sie sicher, dass Sie die Bibliothek Aspose.Slides für .NET installiert haben. Wenn Sie dies noch nicht getan haben, können Sie es von der[Aspose.Slides für .NET-Dokumentation](https://reference.aspose.com/slides/net/).

### PowerPoint-Präsentation mit Audio-Hyperlinks

Sie benötigen eine PowerPoint-Präsentation (PPTX), die Hyperlinks mit zugehörigem Audio enthält. Diese Präsentation dient als Quelle für die Audioextraktion.

## Importieren erforderlicher Namespaces

Um Aspose.Slides für .NET effektiv zu nutzen, müssen Sie die folgenden Namespaces in Ihr C#-Projekt importieren:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Nachdem wir nun alles vorbereitet haben, unterteilen wir den Extraktionsprozess in einfache Schritte.

## Schritt 1: Definieren Sie das Dokumentverzeichnis

 Geben Sie zunächst das Verzeichnis an, in dem sich Ihre PowerPoint-Präsentation befindet. Ersetzen Sie`"Your Document Directory"` mit dem tatsächlichen Pfad.

```csharp
string dataDir = "Your Document Directory";
```

## Schritt 2: Laden Sie die PowerPoint-Präsentation

 Laden Sie als nächstes die PowerPoint-Präsentation (PPTX), die den Audio-Hyperlink enthält. Ersetzen Sie`"HyperlinkSound.pptx"` durch den tatsächlichen Dateinamen Ihrer Präsentation.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Fahren Sie mit dem nächsten Schritt fort.
}
```

## Schritt 3: Zugriff auf den Hyperlink-Sound

Rufen Sie den Hyperlink aus der ersten Form auf der ersten Folie ab. Wenn diesem Hyperlink ein Ton zugeordnet ist, können wir mit dem Extrahieren fortfahren.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Fahren Sie mit dem nächsten Schritt fort.
}
```

## Schritt 4: Audio aus dem Hyperlink extrahieren

Wenn der Hyperlink Ton enthält, können wir ihn als Byte-Array extrahieren und als Mediendatei speichern.

```csharp
// Extrahieren des Hyperlink-Sounds als Byte-Array
byte[] audioData = link.Sound.BinaryData;

// Geben Sie den Pfad an, in dem Sie das extrahierte Audio speichern möchten
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Speichern Sie das extrahierte Audio in einer Mediendatei
File.WriteAllBytes(outMediaPath, audioData);
```

Herzlichen Glückwunsch! Sie haben mit Aspose.Slides für .NET erfolgreich Audio aus einem Hyperlink in einer PowerPoint-Präsentation extrahiert. Sie können dieses Audio jetzt in Ihren Multimediaprojekten verwenden.

## Abschluss

Aspose.Slides für .NET bietet eine leistungsstarke und benutzerfreundliche Möglichkeit, Audio aus Hyperlinks in PowerPoint-Präsentationen zu extrahieren. Mit den in diesem Handbuch beschriebenen Schritten können Sie Audioinhalte aus Ihren Präsentationen problemlos wiederverwenden, um Ihre Projekte zu verbessern.

## Häufig gestellte Fragen

### Ist Aspose.Slides für .NET eine kostenlose Bibliothek?
 Nein, Aspose.Slides für .NET ist eine kommerzielle Bibliothek, aber Sie können eine kostenlose Testversion herunterladen, um die Funktionen zu erkunden von[Hier](https://releases.aspose.com/).

### Kann ich Audio aus älteren PowerPoint-Formaten wie PPT extrahieren?
Ja, Aspose.Slides für .NET unterstützt sowohl PPTX- als auch PPT-Formate für die Audioextraktion.

### Gibt es ein Community-Forum für Aspose.Slides-Support?
 Auf jeden Fall! Hilfe und Erfahrungsaustausch gibt es im[Aspose.Slides-Community-Forum](https://forum.aspose.com/).

### Kann ich für ein kurzfristiges Projekt eine temporäre Lizenz für Aspose.Slides erwerben?
Ja, Sie können eine temporäre Lizenz für Ihre kurzfristigen Projektanforderungen erhalten, indem Sie[dieser Link](https://purchase.aspose.com/temporary-license/).

### Werden für die Extraktion außer MPG noch andere Audioformate unterstützt?
Ja, Aspose.Slides für .NET ermöglicht die Extraktion in verschiedene Audioformate. Sie können das Audio nach der Extraktion in Ihr bevorzugtes Format konvertieren.