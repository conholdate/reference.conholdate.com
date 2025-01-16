---
title: Extrahieren Sie Videos aus PowerPoint-Folien mit Aspose.Slides
linktitle: Extrahieren Sie Videos aus PowerPoint-Folien
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Entdecken Sie, wie Sie mit Aspose.Slides für .NET ganz einfach eingebettete Videodateien aus PowerPoint-Präsentationen extrahieren. Diese umfassende Schritt-für-Schritt-Anleitung deckt alles ab, vom Einrichten Ihrer Umgebung bis zum Speichern der extrahierten Videos.
type: docs
weight: 14
url: /de/net/tutorials/slides/extract-audio-and-video/extract-videos-from-powerpoint-slides/
---
## Einführung

Aspose.Slides für .NET ist eine leistungsstarke Bibliothek, die es Entwicklern ermöglicht, programmgesteuert mit PowerPoint-Präsentationen zu interagieren. In dieser Anleitung führen wir Sie durch den Prozess des Extrahierens von in PowerPoint-Folien eingebetteten Videos mit Aspose.Slides für .NET. 

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Slides für .NET: Beziehen und installieren Sie die Bibliothek von der[Aspose-Website](https://purchase.aspose.com/buy).
-  PowerPoint-Präsentation: Bereiten Sie eine PowerPoint-Datei vor (z. B.`Video.pptx`) mit dem Video, das Sie extrahieren möchten.

## Erforderliche Namespaces

Um mit Aspose.Slides für .NET zu arbeiten, müssen Sie die entsprechenden Namespaces importieren. Fügen Sie Folgendes in Ihren Code ein:

```csharp
using Aspose.Slides;
using Aspose.Slides.Video;
```

## Schritt 1: Dokumentverzeichnis festlegen

Legen Sie zunächst den Pfad zu Ihrer PowerPoint-Präsentation fest:

```csharp
string dataDir = "Your Document Directory";
```

 Ersetzen`"Your Document Directory"` durch den tatsächlichen Pfad zum Verzeichnis, das Ihre PowerPoint-Datei enthält.

## Schritt 2: Laden Sie die Präsentation

 Laden Sie die PowerPoint-Präsentation in ein`Presentation` Objekt:

```csharp
Presentation presentation = new Presentation(dataDir + "Video.pptx");
```

 Dies initialisiert den`Presentation` Objekt mit Ihrer angegebenen PowerPoint-Datei.

## Schritt 3: Durch Folien und Formen iterieren

Gehen Sie als Nächstes jede Folie der Präsentation durch und suchen Sie nach Videobildern:

```csharp
foreach (ISlide slide in presentation.Slides)
{
    foreach (IShape shape in slide.Shapes)
    {
        if (shape is VideoFrame videoFrame)
        {
            // Fahren Sie mit dem Extrahieren des Videos fort
        }
    }
}
```

## Schritt 4: Videodaten extrahieren

Wenn Sie ein Videobild gefunden haben, extrahieren Sie dessen Eigenschaften und Binärdaten:

```csharp
IVideoFrame vf = (IVideoFrame)shape;  // Speichern Sie die Form als Videobild
string contentType = vf.EmbeddedVideo.ContentType;
Byte[] buffer = vf.EmbeddedVideo.BinaryData;

// Holen Sie sich die Dateierweiterung
string fileExtension = contentType.Substring(contentType.LastIndexOf('/') + 1);
```

## Schritt 5: Speichern Sie das Video

Zum Schluss schreiben Sie die extrahierten Videodaten in eine Datei:

```csharp
using (FileStream stream = new FileStream(dataDir + "ExtractedVideo." + fileExtension, FileMode.Create, FileAccess.Write, FileShare.Read))
{
    stream.Write(buffer, 0, buffer.Length);
}
```

Dieser Code erstellt eine neue Datei in Ihrem angegebenen Verzeichnis und schreibt die Videodaten hinein.

## Abschluss

Mit Aspose.Slides für .NET ist das Extrahieren von Videos aus PowerPoint-Folien ein unkomplizierter Vorgang. Wenn Sie dieser Anleitung folgen, können Sie Multimedia-Inhalte problemlos in Ihren .NET-Anwendungen verwalten und so das Benutzererlebnis und die Funktionalität verbessern.

## Häufig gestellte Fragen

### Was ist Aspose.Slides für .NET?
Aspose.Slides für .NET ist eine Bibliothek für die Arbeit mit PowerPoint-Präsentationen, die es Benutzern ermöglicht, Präsentationsdateien programmgesteuert zu erstellen, zu bearbeiten und zu bearbeiten.

### Wo finde ich die Dokumentation für Aspose.Slides für .NET?
 Sie können auf die vollständige Dokumentation zugreifen[Hier](https://reference.aspose.com/slides/net/).

### Ist Aspose.Slides für .NET als kostenlose Testversion verfügbar?
 Ja, Sie können eine kostenlose Testversion herunterladen von[dieser Link](https://releases.aspose.com/).

### Wie kann ich eine temporäre Lizenz für Aspose.Slides für .NET erhalten?
 Anträge auf temporäre Lizenzen können gestellt werden[Hier](https://purchase.aspose.com/temporary-license/).

### Wo erhalte ich Support für Aspose.Slides für .NET?
 Support erhalten Sie über die[Aspose.Slides-Forum](https://forum.aspose.com/).