---
title: Speichern von OneNote-Dokumenten im PDF-Format mit Aspose.Note für .NET
linktitle: OneNote-Dokumente im PDF-Format speichern
second_title: Aspose.Note .NET-API
description: Erfahren Sie, wie Sie Microsoft OneNote-Dokumente mit Aspose.Note für .NET effizient als PDF-Dateien speichern. Dieser Leitfaden führt Sie durch die erforderlichen Voraussetzungen und bietet hilfreiche FAQs.
type: docs
weight: 26
url: /de/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Einführung

In diesem Tutorial erfahren Sie, wie Sie Dokumente mit Aspose.Note für .NET im PDF-Format speichern. Aspose.Note ist eine leistungsstarke Bibliothek, mit der Entwickler programmgesteuert mit Microsoft OneNote-Dateien arbeiten können. Wir behandeln die Voraussetzungen, importieren Namespaces und bieten Schritt-für-Schritt-Anleitungen zum Speichern von Dokumenten im PDF-Format in verschiedenen Seitenlayouts.

## Voraussetzungen
1. Visual Studio: Stellen Sie sicher, dass es installiert ist.
2. Aspose.Note für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie.
3. C#-Kenntnisse: Grundlegende Kenntnisse der Sprache sind erforderlich.

## Erforderliche Namespaces importieren
Bevor Sie fortfahren, importieren Sie die folgenden Namespaces in Ihren Code:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Schritt 1: Als PDF mit den Letter-Seiteneinstellungen speichern
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Aktualisieren Sie diesen Pfad
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Lädt das OneNote-Dokument und speichert es als PDF mit Seiteneinstellungen im Letter-Format.

## Schritt 2: Als PDF mit A4-Seiteneinstellungen speichern (keine Höhenbeschränkung)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Aktualisieren Sie diesen Pfad
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Ähnlich wie Schritt 1, verwendet jedoch A4-Seiteneinstellungen ohne Höhenbeschränkungen.

## Abschluss
Das Tutorial zeigt erfolgreich, wie man OneNote-Dateien mit Aspose.Note in das PDF-Format konvertiert. Durch die Verwendung verschiedener Seiteneinstellungen gewinnen Entwickler Flexibilität bei der Dokumentenverwaltung.

## Häufig gestellte Fragen
### Kann Aspose.Note komplexe OneNote-Dateien verarbeiten?
Ja, es verarbeitet effektiv verschiedene Funktionen komplexer OneNote-Dateien.

### Ist Aspose.Note für kommerzielle Projekte geeignet?
Ja, Sie können es nach dem Erwerb einer Lizenz für kommerzielle Anwendungen verwenden.

### Bietet Aspose.Note eine kostenlose Testversion an?
Ja, es steht eine kostenlose Testversion zum Ausprobieren zur Verfügung.

### Wo finde ich Dokumentation für Aspose.Note?
Eine ausführliche Dokumentation ist auf der Aspose-Referenzsite verfügbar.

### Benötigen Sie weitere Hilfe?
Bei Fragen und für Support wenden Sie sich an das Aspose.Note-Forum.
