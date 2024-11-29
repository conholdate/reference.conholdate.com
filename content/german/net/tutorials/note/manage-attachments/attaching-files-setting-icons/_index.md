---
title: Anhängen von Dateien und Festlegen von Symbolen in Aspose.Note für .NET
linktitle: Datei anhängen und Symbol in Aspose.Note festlegen
second_title: Aspose.Note .NET-API
description: Erfahren Sie Schritt für Schritt, wie Sie mit Aspose.Note für .NET Dateien anhängen und benutzerdefinierte Symbole in Microsoft OneNote-Dokumenten festlegen. Erweitern Sie Ihre .NET-Anwendung mit nahtlosen Dokumentverwaltungs- und Anpassungsfunktionen.
type: docs
weight: 10
url: /de/net/tutorials/note/manage-attachments/attaching-files-setting-icons/
---
## Einführung

Aspose.Note für .NET ist eine erweiterte Bibliothek, die für Entwickler entwickelt wurde, um Microsoft OneNote-Dateien programmgesteuert zu erstellen, zu bearbeiten und zu konvertieren. Ein herausragendes Merkmal dieser Bibliothek ist die Möglichkeit, Dateien an OneNote-Dokumente anzuhängen und deren Symbole anzupassen. In diesem Handbuch erfahren Sie, wie Sie Aspose.Note für .NET nutzen können, um nahtlos Dateien anzuhängen und benutzerdefinierte Symbole festzulegen und so die Funktionalität Ihres OneNote-Dokuments zu erweitern.

## Voraussetzungen

Stellen Sie vor der Implementierung der Lösung sicher, dass Sie über Folgendes verfügen:

- Entwicklungsumgebung: Visual Studio oder eine ähnliche IDE, die für die .NET-Entwicklung konfiguriert ist.
-  Installation der Bibliothek: Installieren Sie die[Aspose.Note für .NET](https://releases.aspose.com/words/net/) Bibliothek.
- Programmierkenntnisse: Grundlegende Kenntnisse in C#.

## Importieren erforderlicher Namespaces

Fügen Sie Ihrem Projekt für grundlegende Funktionen diese Namespaces hinzu:

```csharp
using System.IO;
using Aspose.Note;
using System;
using System.Collections.Generic;
using System.Drawing.Imaging;
```

Nachfolgend finden Sie die detaillierte Schritt-für-Schritt-Implementierung.

## Schritt 1: Erstellen Sie ein neues OneNote-Dokument

 Initialisieren Sie ein neues OneNote-Dokument mit dem`Document` Klasse.

```csharp
Document doc = new Document();
```

## Schritt 2: Eine neue Seite hinzufügen

Fügen Sie dem Dokument eine Seite hinzu, um Ihre Notizen und Anhänge zu organisieren.

```csharp
Aspose.Note.Page page = new Aspose.Note.Page(doc);
```

## Schritt 3: Erstellen Sie eine Gliederung

 Erstellen Sie ein`Outline` Objekt, das als Container für Elemente auf Ihrer OneNote-Seite dient.

```csharp
Outline outline = new Outline(doc);
```

## Schritt 4: Initialisieren eines Gliederungselements

 Ein`OutlineElement` enthält den Anhang und das zugehörige Symbol.

```csharp
OutlineElement outlineElem = new OutlineElement(doc);
```

## Schritt 5: Eine Datei anhängen und ihr Symbol angeben

Geben Sie die anzuhängende Datei an und legen Sie ein Symbol dafür fest.

```csharp
string dataDir = "Your Document Directory";

using (var stream = File.OpenRead(dataDir + "icon.jpg"))
{
    AttachedFile attachedFile = new AttachedFile(doc, dataDir + "attachment.txt", stream, ImageFormat.Jpeg);
    outlineElem.AppendChildLast(attachedFile);
}
```

## Schritt 6: Erstellen Sie die Dokumentstruktur

 Fügen Sie den`OutlineElement` zur`Outline` und die`Outline` zur`Page`.

```csharp
outline.AppendChildLast(outlineElem);
page.AppendChildLast(outline);
```

## Schritt 7: Seite zum Dokument hinzufügen

Fügen Sie die Seite abschließend in Ihr OneNote-Dokument ein.

```csharp
doc.AppendChildLast(page);
```

## Schritt 8: Speichern Sie das Dokument

Exportieren Sie Ihr aktualisiertes Dokument mit dem Dateianhang und dem Symbol.

```csharp
dataDir = dataDir + "AttachFileAndSetIcon_out.one";
doc.Save(dataDir);
```

## Abschluss

Wenn Sie die in diesem Handbuch beschriebenen Schritte befolgen, können Sie mit Aspose.Note für .NET mühelos Dateien anhängen und benutzerdefinierte Symbole in OneNote-Dokumenten festlegen. Diese Funktion kann die Dokumentorganisation und das Benutzererlebnis erheblich verbessern und Ihre Anwendungen robuster und funktionsreicher machen.

## Häufig gestellte Fragen

### Können einer einzelnen Notiz mehrere Dateien angehängt werden?
Ja, Sie können mehrere Dateien anhängen, indem Sie den Anhängevorgang für jede Datei wiederholen.

### Welche Bildformate werden für Symbole unterstützt?
Aspose.Note unterstützt die Formate JPEG, PNG, BMP und GIF für Anhangssymbole.

### Ist es möglich, Dateien dynamisch von externen URLs anzuhängen?
 Sie können Dateien mit .NET-Bibliotheken herunterladen wie`HttpClient` und hängen Sie sie dann mit Aspose.Note an.

### Gibt es Beschränkungen hinsichtlich der Dateigröße von Anhängen?
Aspose.Note legt keine explizite Größenbeschränkung fest, Sie sollten jedoch sicherstellen, dass Ihre Systemressourcen große Dateien verarbeiten können.

### Kann die Größe von Symbolen vor dem Festlegen geändert werden?
Ja, Sie können das Symbolbild mit .NET bearbeiten.`System.Drawing` Bibliothek, bevor Sie sie anhängen.

 Weitere Hilfe finden Sie im[Dokumentation](https://reference.aspose.com/words/net/) oder wenden Sie sich an[Aspose-Unterstützung](https://forum.aspose.com/c/words/8).