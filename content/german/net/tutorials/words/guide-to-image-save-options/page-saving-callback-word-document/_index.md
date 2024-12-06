---
title: Rückruf zum Speichern von Seiten in Word-Dokumenten
linktitle: Rückruf zum Speichern von Seiten in Word-Dokumenten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET jede Seite eines Word-Dokuments ganz einfach in einzelne PNG-Bilder konvertieren. Diese Anleitung enthält schrittweise Anweisungen, einschließlich Codebeispielen.
type: docs
weight: 10
url: /de/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Einführung

Mussten Sie schon einmal jede Seite eines Word-Dokuments in einzelne Bilder umwandeln? Egal, ob Sie Miniaturansichten für eine Vorschau erstellen oder einen langen Bericht in verständliche Bilder aufteilen möchten, Aspose.Words für .NET macht diese Aufgabe einfach und effizient. In dieser Anleitung führen wir Sie durch den Prozess der Einrichtung eines seitenspeichernden Rückrufs, um jede Seite Ihres Dokuments als PNG-Bild zu speichern. Lassen Sie uns anfangen!

## Voraussetzungen

Stellen Sie vor dem Eintauchen sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Laden Sie es herunter und installieren Sie es von[Hier](https://releases.aspose.com/words/net/).
2. Visual Studio: Jede Version funktioniert, aber wir verwenden für dieses Handbuch Visual Studio 2019.
3. Grundlegende C#-Kenntnisse: Wenn Sie mit C# vertraut sind, können Sie problemlos mitmachen.

## Schritt 1: Erforderliche Namespaces importieren

Zuerst müssen wir die erforderlichen Namespaces importieren. Dadurch können wir auf die erforderlichen Klassen und Methoden zugreifen, ohne jedes Mal den vollständigen Namespace eingeben zu müssen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 2: Definieren Sie Ihr Dokumentverzeichnis

Legen Sie als nächstes den Pfad zu Ihrem Dokumentverzeichnis fest. Hier befindet sich Ihr Word-Eingabedokument und hier werden auch die Ausgabebilder gespeichert.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 3: Laden Sie Ihr Dokument

Laden wir nun das Dokument, das Sie verarbeiten möchten. Stellen Sie sicher, dass sich Ihr Dokument mit dem Namen „Rendering.docx“ im angegebenen Verzeichnis befindet.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 4: Optionen zum Speichern von Bildern konfigurieren

Wir richten die Optionen zum Speichern von Bildern ein und geben an, dass wir die Seiten als PNG-Dateien speichern möchten.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Hier,`PageSet` definiert den zu speichernden Seitenbereich und`PageSavingCallback` verweist auf unsere benutzerdefinierte Rückrufklasse.

## Schritt 5: Implementieren des Rückrufs zum Speichern der Seite

Jetzt müssen wir die Rückrufklasse implementieren, die regelt, wie jede Seite gespeichert wird.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Diese Klasse implementiert die`IPageSavingCallback` Schnittstelle. Im`PageSaving` Methode geben wir das Benennungsmuster für jede gespeicherte Seite an.

## Schritt 6: Speichern Sie das Dokument als Bilder

Abschließend speichern wir das Dokument mit den konfigurierten Optionen.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich einen Rückruf zum Speichern von Seiten eingerichtet, um jede Seite eines Word-Dokuments mit Aspose.Words für .NET als separates PNG-Bild zu speichern. Diese Technik ist für verschiedene Anwendungen unglaublich nützlich, vom Erstellen von Seitenvorschauen bis zum Generieren einzelner Seitenbilder für Berichte.

## Häufig gestellte Fragen

### Kann ich Seiten in anderen Formaten als PNG speichern?
 Ja! Sie können Seiten InFormaten wie JPEG, BMP und TIFF speichern, indem Sie die`SaveFormat` in `ImageSaveOptions`.

### Wie kann ich nur bestimmte Seiten speichern?
 Um bestimmte Seiten zu speichern, passen Sie die`PageSet` Parameter in`ImageSaveOptions` um nur die gewünschten Seiten einzuschließen.

### Ist es möglich, die Bildqualität anzupassen?
 Absolut! Sie können die Qualität des Ausgabebildes steuern, indem Sie Eigenschaften wie`ImageSaveOptions.JpegQuality`.

### Wie kann ich große Dokumente effizient verarbeiten?
Erwägen Sie bei großen Dokumenten die Stapelverarbeitung der Seiten, um die Speichernutzung effektiv zu verwalten.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?
 Ausführliche Anleitungen und Beispiele finden Sie im[Aspose.Words-Dokumentation](https://reference.aspose.com/words/net/).