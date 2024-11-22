---
title: Anleitung zur OCR-Erkennung von Bildern aus URLs in der OCR-Bilderkennung
linktitle: Anleitung zur OCR-Erkennung von Bildern aus URLs in der OCR-Bilderkennung
second_title: Aspose.OCR .NET API
description: Entdecken Sie, wie Sie mit Aspose.OCR mühelos optische Zeichenerkennung (OCR) in Ihre .NET-Anwendungen implementieren. Diese Schritt-für-Schritt-Anleitung führt Sie durch den gesamten Prozess.
type: docs
weight: 10
url: /de/net/tutorials/ocr/optimization-ocr/guide-to-ocr-on-image-from-url/
---
## Einführung

Optische Zeichenerkennung (OCR) ist eine wichtige Technologie zum Extrahieren von Text aus Bildern. Sie ermöglicht es Entwicklern, Anwendungen zu erstellen, die Textinformationen nahtlos lesen und verarbeiten können. Aspose.OCR für .NET ist eine robuste Bibliothek, die die Integration von OCR-Funktionen in Ihre .NET-Anwendungen vereinfacht. Diese Anleitung zeigt, wie Sie in nur wenigen einfachen Schritten OCR auf einem Bild direkt von einer URL aus durchführen.

## Voraussetzungen

Stellen Sie vor dem Start sicher, dass die folgenden Voraussetzungen erfüllt sind:

-  Aspose.OCR für .NET: Laden Sie die Aspose.OCR-Bibliothek herunter und integrieren Sie sie in Ihr .NET-Projekt aus dem[Veröffentlichungsseite](https://releases.aspose.com/ocr/net/).
- Entwicklungsumgebung: Richten Sie auf Ihrem Computer eine .NET-Entwicklungsumgebung ein (Visual Studio wird empfohlen).

## Schritt 1: Erforderliche Namespaces importieren

Um die von Aspose.OCR angebotenen Funktionen zu nutzen, importieren Sie die erforderlichen Namespaces in Ihr Projekt:

```csharp
using System;
using System.Collections.Generic;
using System.Drawing;
using System.IO;
using Aspose.OCR;
using Aspose.OCR.Models;
```

## Schritt 2: Dokumentverzeichnis angeben

 Definieren Sie ein Verzeichnis für Ihre Dokumente. Ersetzen Sie`"Your Document Directory"` mit dem Pfad zu Ihrem Arbeitsverzeichnis:

```csharp
string dataDir = "Your Document Directory";
```

## Schritt 3: Geben Sie die Bild-URL an

Geben Sie die URL des Bildes an, aus dem Sie Text extrahieren möchten. Stellen Sie sicher, dass das Bild öffentlich zugänglich ist:

```csharp
string uri = "https://beispiel.com/bild.jpg";
```

## Schritt 4: Aspose.OCR initialisieren

 Erstellen Sie eine Instanz des`AsposeOcr` Klasse, die Sie zum Ausführen des OCR-Vorgangs verwenden:

```csharp
AsposeOcr api = new AsposeOcr();
```

## Schritt 5: Text aus Bild erkennen

 Verwenden Sie die`RecognizeImageFromUri` Methode zum Extrahieren von Text aus der Bild-URL. Sie können verschiedene Erkennungseinstellungen basierend auf Ihren spezifischen Anforderungen anpassen:

```csharp
RecognitionResult result = api.RecognizeImageFromUri(uri, new RecognitionSettings
{
    DetectAreas = true,
    RecognizeSingleLine = false,
    AutoSkew = true,
    RecognitionAreas = new List<Rectangle>
    {
        new Rectangle(1, 3, 390, 70),
        new Rectangle(1, 72, 390, 70)
    }
});
```

## Schritt 6: Anzeige der Erkennungsergebnisse

Geben Sie den erkannten Text zusammen mit allen relevanten Informationen aus, einschließlich erkannter Bereiche und Warnungen:

```csharp
Console.WriteLine($"Text:\n {result.RecognitionText}");
Console.WriteLine("Areas:");
result.RecognitionAreasText.ForEach(a => Console.WriteLine($"{a}"));
Console.WriteLine("Warnings:");
result.Warnings.ForEach(w => Console.WriteLine($"{w}"));
Console.WriteLine($"JSON: {result.GetJson()}");
```

## Schritt 7: Führen Sie Ihre Anwendung aus

Führen Sie Ihre Anwendung aus. Wenn alles richtig konfiguriert ist, sollte der OCR-Prozess erfolgreich ausgeführt werden:

```csharp
Console.WriteLine("OCR process executed successfully.");
```

## Abschluss

Mit Aspose.OCR ist die Integration von OCR-Funktionen in Ihre .NET-Anwendungen ganz einfach. Dieser Leitfaden hat Sie durch die entscheidenden Schritte zur Durchführung von OCR auf einem Bild von einer URL geführt und eine Grundlage für die Entwicklung von Anwendungen geschaffen, die Texterkennungstechnologie nutzen.

## Häufig gestellte Fragen

### Ist Aspose.OCR zum Erkennen mehrerer Sprachen geeignet?

Ja, Aspose.OCR unterstützt verschiedene Sprachen und ist daher ideal für Anwendungen, die sich an internationale Benutzer richten.

### Kann Aspose.OCR sowohl einzeilige als auch mehrzeilige Texterkennung verarbeiten?

Auf jeden Fall! Die Bibliothek ist vielseitig und ermöglicht je nach den Anforderungen Ihres Projekts sowohl die Erkennung einzeiliger als auch mehrzeiliger Texte.

### Welche Lizenzierungsoptionen sind für Aspose.OCR verfügbar?

 Sie können sich über die verschiedenen Lizenzierungsoptionen informieren und Käufe tätigen über[Aspose Store](https://purchase.conholdate.com/buy).

### Gibt es eine Testversion von Aspose.OCR?

 Ja, eine kostenlose Testversion ist verfügbar. Sie können sie auf der[Veröffentlichungsseite](https://releases.aspose.com/).

### Wo finde ich Unterstützung für Aspose.OCR?

Für Hilfe oder Community-Diskussionen über Aspose.OCR besuchen Sie die[Aspose.OCR Forum](https://forum.aspose.com/c/ocr/16).