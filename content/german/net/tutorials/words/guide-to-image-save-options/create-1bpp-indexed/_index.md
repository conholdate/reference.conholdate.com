---
title: Erstellen Sie 1Bpp Indexed
linktitle: Erstellen Sie 1Bpp Indexed
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Dieses Handbuch enthält Schritt-für-Schritt-Anleitungen und Beispielcode, mit deren Hilfe Sie effizient indizierte 1-Bpp-Bilder zum Archivieren, Drucken oder zur Platzersparnis erstellen können.
type: docs
weight: 10
url: /de/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Einführung

Mussten Sie schon einmal ein Word-Dokument in ein Schwarzweißbild umwandeln? Ob für die digitale Archivierung, den Druck oder einfach zum Platzsparen, die Konvertierung Ihrer Dokumente in ein 1Bpp-indiziertes Bild kann unglaublich nützlich sein. In dieser Anleitung zeigen wir Ihnen eine einfache Methode, um dies mit Aspose.Words für .NET zu erreichen. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor Sie in den Code eintauchen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Words für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.aspose.com/words/net/).
- .NET-Entwicklungsumgebung: Visual Studio ist eine beliebte Wahl, jedoch ist jede IDE, die .NET unterstützt, geeignet.
- Grundlegende C#-Kenntnisse: Kenntnisse in C# sind hilfreich, aber wir halten die Dinge einfach.
- Beispiel-Word-Dokument: Halten Sie ein Dokument zur Konvertierung bereit.

## Schritt 1: Erforderliche Namespaces importieren

Um Aspose.Words zu verwenden, müssen Sie die entsprechenden Namespaces importieren. Dies ist für den Zugriff auf die für die Dokumentbearbeitung erforderlichen Klassen und Methoden unerlässlich.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 2: Richten Sie Ihr Dokumentverzeichnis ein

Geben Sie den Pfad zum Verzeichnis an, in dem Ihr Word-Dokument gespeichert ist und in dem Sie das konvertierte Bild speichern möchten.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Schritt 3: Laden Sie das Word-Dokument

Laden Sie Ihr Word-Dokument in ein`Aspose.Words.Document` Objekt. Mit diesem Objekt können Sie das Dokument programmgesteuert bearbeiten.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 4: Optionen zum Speichern von Bildern konfigurieren

 Richten Sie als Nächstes die`ImageSaveOptions` um zu definieren, wie das Dokument als Bild gespeichert wird. Wir konfigurieren es so, dass es im PNG-Format mit indiziertem 1Bpp-Farbmodus gespeichert wird.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Konvertieren Sie nur die erste Seite
    ImageColorMode = ImageColorMode.BlackAndWhite, // Auf Schwarzweiß einstellen
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Verwenden Sie das indizierte 1Bpp-Format
};
```

- SaveFormat.Png: Gibt an, dass das Ausgabeformat PNG sein wird.
- PageSet(1): Gibt an, dass nur die erste Seite des Dokuments konvertiert wird.
- ImageColorMode.BlackAndWhite: Stellt sicher, dass das Bild schwarzweiß ist.
- ImagePixelFormat.Format1bppIndexed: Legt das Pixelformat auf 1Bpp indiziert fest und optimiert so den Platz.

## Schritt 5: Speichern Sie das Dokument als Bild

 Verwenden Sie abschließend die`Save` Methode der`Document` Objekt, um das konvertierte Bild zu speichern.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben ein Word-Dokument mithilfe von Aspose.Words für .NET erfolgreich in ein 1Bpp-indiziertes Bild konvertiert. Diese Methode ist nicht nur effizient, sondern hilft Ihnen auch dabei, kontrastreiche Bilder zu erstellen, die für verschiedene Anwendungen geeignet sind. Sie können diese Funktionalität gerne in Ihre Projekte integrieren. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist ein 1Bpp-indexiertes Bild?
Ein mit 1 Bpp (1 Bit pro Pixel) indiziertes Bild ist ein Schwarzweiß-Bildformat, bei dem jedes Pixel durch ein einzelnes Bit, entweder 0 oder 1, dargestellt wird. Dieses Format ist äußerst platzsparend und eignet sich daher ideal zum Archivieren.

### Kann ich mehrere Seiten eines Word-Dokuments auf einmal konvertieren?
 Ja! Ändern Sie einfach die`PageSet` Eigentum in der`ImageSaveOptions` um mehrere Seiten einzuschließen oder die Konvertierung des gesamten Dokuments einzustellen.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
 Ja, für die volle Funktionalität ist eine Lizenz erforderlich. Sie erhalten eine[vorläufige Lizenz hier](https://purchase.aspose.com/temporary-license/).

### In welche anderen Bildformate kann ich mein Word-Dokument konvertieren?
 Aspose.Words unterstützt verschiedene Formate, darunter JPEG, BMP und TIFF. Ändern Sie einfach die`SaveFormat`im`ImageSaveOptions` in das gewünschte Format.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
 Eine umfassende Dokumentation finden Sie unter[Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).