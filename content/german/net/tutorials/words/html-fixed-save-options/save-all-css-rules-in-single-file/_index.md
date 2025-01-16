---
title: Alle CSS-Regeln in einer einzigen Datei speichern
linktitle: Schreiben Sie alle CSS-Regeln in eine einzige Datei
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET alle CSS-Regeln in eine einzige Datei schreiben, wenn Sie Dokumente mit HtmlFixedSaveOptions speichern. Folgen Sie diesem ausführlichen Tutorial für eine Schritt-für-Schritt-Anleitung.
type: docs
weight: 10
url: /de/net/tutorials/words/html-fixed-save-options/save-all-css-rules-in-single-file/
---
## Einführung

Haben Sie beim Konvertieren von Word-Dokumenten in HTML schon einmal mit einer unübersichtlichen Reihe von CSS-Regeln gekämpft? Damit sind Sie nicht allein! Glücklicherweise bietet Aspose.Words für .NET eine leistungsstarke Funktion, mit der Sie alle Ihre CSS-Regeln in einer einzigen Datei konsolidieren können. Dies bereinigt nicht nur Ihren Code, sondern vereinfacht auch Ihren Arbeitsablauf. Begeben wir uns auf eine Reise hin zu saubererer, effizienterer HTML-Ausgabe!

## Voraussetzungen

Bevor wir mit der Codierung beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET: Beziehen Sie die Bibliothek von[Hier](https://releases.aspose.com/words/net/).
2. .NET-Entwicklungsumgebung: Für die Entwicklung ist ein Setup wie Visual Studio ideal.
3. Grundlegende C#-Kenntnisse: Die Vertrautheit mit C# erleichtert Ihnen die Navigation im Code.
4. Word-Dokument: Halten Sie eine DOCX-Datei zur Konvertierung bereit.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces in Ihr C#-Projekt. Dadurch können wir problemlos auf die Aspose.Words-Funktionen zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Um eine reibungslose Konvertierung zu gewährleisten, unterteilen wir diesen Vorgang in überschaubare Schritte.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Legen Sie zunächst den Verzeichnispfad fest, in dem sich Ihr Word-Dokument befindet und in dem das konvertierte HTML gespeichert wird.

```csharp
// Definieren Sie den Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Schritt 2: Laden Sie das Word-Dokument

 Laden Sie anschließend das Word-Dokument mit dem`Document` Klasse aus der Aspose.Words-Bibliothek.

```csharp
// Laden Sie das Word-Dokument
Document doc = new Document(dataDir + "Document.docx");
```

## Schritt 3: HTML-Speicheroptionen konfigurieren

 Nun konfigurieren wir die HTML-Speicheroptionen. Wir möchten die Funktion aktivieren, die alle CSS-Regeln in einer einzigen Datei konsolidiert, indem wir`SaveFontFaceCssSeparately` Zu`false`.

```csharp
// Konfigurieren Sie die HTML-Speicheroptionen, um alle CSS-Regeln in eine Datei zu schreiben
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Schritt 4: Dokument in HTML konvertieren

Speichern Sie das Dokument abschließend als HTML-Datei mit den angegebenen Optionen. Dadurch wird sichergestellt, dass alle CSS-Regeln übersichtlich in einer einzigen Datei zusammengefasst sind.

```csharp
// Konvertieren Sie das Dokument in HTML
doc.Save(dataDir + "ConvertedDocument.html", saveOptions);
```

## Abschluss

Herzlichen Glückwunsch! Mit nur wenigen Codezeilen haben Sie Ihr Word-Dokument erfolgreich in HTML konvertiert und dabei sichergestellt, dass alle CSS-Regeln sauber in einer einzigen Datei kompiliert sind. Dieser Ansatz vereinfacht die CSS-Verwaltung und verbessert die Wartbarkeit Ihrer HTML-Dokumente. Wenn Sie das nächste Mal ein Word-Dokument konvertieren müssen, steht Ihnen ein optimierter Prozess zur Verfügung!

## Häufig gestellte Fragen

### Warum sollte ich für meine HTML-Ausgabe eine einzelne CSS-Datei verwenden?
Eine einzelne CSS-Datei vereinfacht die Stilverwaltung und macht Ihr HTML übersichtlicher und effizienter zu pflegen.

### Kann ich die CSS-Regeln für Schriftarten bei Bedarf trennen?
 Auf jeden Fall! Indem Sie`SaveFontFaceCssSeparately` Zu`true`, Sie können die CSS-Regeln für Schriftarten in eine andere Datei auslagern.

### Ist die Nutzung von Aspose.Words für .NET kostenlos?
 Aspose.Words bietet eine kostenlose Testversion zum Download an[Hier](https://releases.aspose.com/) . Für die weitere Nutzung sollten Sie den Kauf einer Lizenz in Erwägung ziehen[Hier](https://purchase.aspose.com/buy).

### In welche anderen Formate kann Aspose.Words für .NET konvertieren?
Aspose.Words unterstützt verschiedene Formate, darunter PDF, TXT und Bildformate wie JPEG und PNG.

### Wo finde ich weitere Ressourcen zu Aspose.Words für .NET?
 Ausführliche Anleitungen und API-Referenzen finden Sie im[Dokumentation](https://reference.aspose.com/words/net/).
