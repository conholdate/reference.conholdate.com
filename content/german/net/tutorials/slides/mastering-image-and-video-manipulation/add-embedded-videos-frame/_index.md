---
title: Eingebettete Videorahmen in .NET-Präsentationen hinzufügen
linktitle: Eingebettete Videorahmen in .NET-Präsentationen hinzufügen
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Schöpfen Sie das Potenzial Ihrer Präsentationen aus, indem Sie lernen, wie Sie Videos mit Aspose.Slides für .NET einbetten. Dieses umfassende Tutorial führt Sie Schritt für Schritt durch den Prozess der Integration multimedialer Elemente.
type: docs
weight: 19
url: /de/net/tutorials/slides/mastering-image-and-video-manipulation/add-embedded-videos-frame/
---
## Einführung

In der heutigen schnelllebigen Präsentationswelt kann die Integration von Multimedia-Elementen das Engagement und die Bindung des Publikums erheblich steigern. Aspose.Slides für .NET bietet eine robuste Lösung zum Einbetten von Video-Frames in Ihre Folien. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess und sorgt für ein reibungsloses Erlebnis von Anfang bis Ende.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Slides für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von der[Veröffentlichungsseite](https://releases.aspose.com/slides/net/).
- Medieninhalt: Eine Videodatei (z. B. „Wildlife.mp4“), die Sie in Ihre Präsentation einbetten möchten.

## Erforderliche Namespaces importieren

Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr .NET-Projekt:

```csharp
using System.IO;
using Aspose.Slides;
using Aspose.Slides.Export;
```

## Schritt 1: Richten Sie Ihre Verzeichnisse ein

Stellen Sie sicher, dass Ihr Projekt die erforderlichen Verzeichnisse für Dokument- und Mediendateien enthält:

```csharp
string dataDir = "Your Document Directory";
string videoDir = "Your Media Directory";
string resultPath = Path.Combine(dataDir, "VideoFrame_out.pptx");

// Verzeichnis erstellen, falls es nicht existiert
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);
```

## Schritt 2: Instanziieren der Präsentationsklasse

 Erstellen Sie eine Instanz des`Presentation` Klasse zur Darstellung Ihrer PPTX-Datei:

```csharp
using (Presentation pres = new Presentation())
{
    // Holen Sie sich die erste Folie
    ISlide sld = pres.Slides[0];
```

## Schritt 3: Das Video einbetten

Betten Sie das Video mit dem folgenden Code in Ihre Präsentation ein:

```csharp
IVideo vid = pres.Videos.AddVideo(new FileStream(Path.Combine(videoDir, "Wildlife.mp4"), FileMode.Open), LoadingStreamBehavior.ReadStreamAndRelease);
```

## Schritt 4: Einen Video-Frame hinzufügen

Fügen Sie als Nächstes der Folie einen Video-Frame hinzu:

```csharp
IVideoFrame vf = sld.Shapes.AddVideoFrame(50, 150, 300, 350, vid);
```

## Schritt 5: Videoeigenschaften konfigurieren

Legen Sie die Videoeigenschaften fest, einschließlich Wiedergabemodus und Lautstärke:

```csharp
vf.EmbeddedVideo = vid;
vf.PlayMode = VideoPlayModePreset.Auto; // Video automatisch abspielen
vf.Volume = AudioVolumeMode.Loud; // Lautstärke einstellen
```

## Schritt 6: Speichern Sie Ihre Präsentation

Speichern Sie abschließend die geänderte PPTX-Datei auf der Festplatte:

```csharp
pres.Save(resultPath, SaveFormat.Pptx);
```

Sie können diese Schritte für jedes Video wiederholen, das Sie in Ihre Präsentation einbetten möchten.

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Slides für .NET erfolgreich einen Videorahmen in Ihre Präsentation eingebettet. Diese dynamische Funktion kann Ihre Präsentationen auf die nächste Ebene bringen und Ihr Publikum mit nahtlos integrierten Multimediaelementen fesseln.

## Häufig gestellte Fragen

### Kann ich in jede Folie der Präsentation Videos einbetten?

 Ja, Sie können jede Folie auswählen, indem Sie den Index in`pres.Slides[index]`.

### Welche Videoformate werden unterstützt?

Aspose.Slides unterstützt verschiedene Videoformate, darunter MP4, AVI und WMV.

### Kann ich die Größe und Position des Videorahmens anpassen?

 Absolut! Sie können die Parameter ändern in`AddVideoFrame(x, y, width, height, video)` um Ihren Bedürfnissen gerecht zu werden.

### Gibt es eine Begrenzung für die Anzahl der Videos, die ich einbetten kann?

Die Beschränkung eingebetteter Videos hängt normalerweise von der Kapazität Ihrer Präsentationssoftware ab.

### Wo kann ich weitere Hilfe erhalten oder meine Erfahrungen teilen?

 Besuchen Sie uns gerne im[Aspose.Slides-Forum](https://forum.aspose.com/c/slides/11) für Community-Unterstützung und Diskussionen.