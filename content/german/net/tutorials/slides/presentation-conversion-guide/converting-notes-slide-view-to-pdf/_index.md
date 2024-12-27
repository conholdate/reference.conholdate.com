---
title: Konvertieren der Notes-Folienansicht in PDF mit Aspose.Slides für .NET
linktitle: Konvertieren der Notes-Folienansicht in PDF mit Aspose.Slides für .NET
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Erfahren Sie, wie Sie PowerPoint-Präsentationen mit Notes Slide View mithilfe von Aspose.Slides für .NET mühelos in das PDF-Format konvertieren. Dieses Handbuch enthält detaillierte Anweisungen.
type: docs
weight: 15
url: /de/net/tutorials/slides/presentation-conversion-guide/converting-notes-slide-view-to-pdf/
---
## Einführung

Wenn Sie häufig mit PowerPoint-Präsentationen arbeiten, wissen Sie, wie wichtig es sein kann, Präsentationen mit ausführlichen Notizen zu teilen. Das Konvertieren dieser Präsentationen in ein PDF mit der Notizen-Folienansicht ist eine praktische Möglichkeit, sie leicht zugänglich zu machen. Aspose.Slides für .NET ist eine leistungsstarke Bibliothek, die diese Aufgabe vereinfacht, indem sie Ihnen ermöglicht, Ihre Präsentationen effizient anzupassen und zu exportieren.

## Voraussetzungen

Stellen Sie vor dem Eintauchen sicher, dass Sie die folgenden Anforderungen erfüllen:

-  Entwicklungsumgebung: Installieren[Visual Studio](https://visualstudio.microsoft.com/) oder jede beliebige C#-IDE.
-  Aspose.Slides für .NET-Bibliothek: Laden Sie die Bibliothek herunter von[Hier](https://releases.aspose.com/slides/net/).
-  Präsentationsdatei: Sie haben eine PowerPoint-Datei (z. B.`NotesFile.pptx`) bereit zur Konvertierung.

## Einrichten Ihrer Umgebung

Befolgen Sie diese Schritte, um Ihre Entwicklungsumgebung einzurichten:

1. Neues Projekt erstellen: Öffnen Sie Ihre IDE und erstellen Sie ein neues C#-Konsolenanwendungsprojekt.
2. Aspose.Slides-Referenz hinzufügen: 
- Installieren Sie die Bibliothek mit dem NuGet Package Manager:
 ```
 Install-Package Aspose.Slides.NET
 ```
- Alternativ können Sie die Aspose.Slides-DLL manuell zu Ihrem Projekt hinzufügen.

```csharp
using Aspose.Slides;
```
Ihr Projekt ist jetzt bereit zur Arbeit mit Aspose.Slides für .NET.

## Laden der Präsentation

Laden Sie zunächst Ihre PowerPoint-Datei in Ihre Anwendung. Hier ist der Code dazu:

```csharp
string dataDir = "Your Document Directory";
using (Presentation presentation = new Presentation(dataDir + "NotesFile.pptx"))
{
	// Weiterer Code kommt hierhin
}

```

 Ersetzen`"Your Document Directory"` durch den Pfad zum Ordner, der Ihre Präsentationsdatei enthält.

## Konfigurieren von PDF-Optionen

 Um die Notizen-Folienansicht in Ihr PDF einzubinden, konfigurieren Sie die`PdfOptions` Objekt wie unten gezeigt:

```csharp
PdfOptions pdfOptions = new PdfOptions();
INotesCommentsLayoutingOptions options = pdfOptions.NotesCommentsLayouting;

// Festlegen der Position der Notizen im Ausgabe-PDF
options.NotesPosition = NotesPositions.BottomFull;
```

Diese Konfiguration stellt sicher, dass in der PDF-Ausgabe Notizen unter den Folien angezeigt werden.

## Speichern der Präsentation als PDF

Sobald Sie Ihre Optionen konfiguriert haben, speichern Sie die Präsentation als PDF. So geht's:

```csharp
presentation.Save(dataDir + "Pdf_Notes_out.pdf", SaveFormat.Pdf, pdfOptions);
```

 Dadurch wird eine PDF-Datei mit dem Namen generiert`Pdf_Notes_out.pdf`in Ihrem angegebenen Verzeichnis, das Folien und die dazugehörigen Notizen enthält.

## Abschluss

Und das war’s! Sie haben eine PowerPoint-Präsentation mit Notes-Folienansicht erfolgreich mit Aspose.Slides für .NET in eine PDF-Datei konvertiert. Dieser Ansatz spart nicht nur Zeit, sondern bietet auch eine zuverlässige und skalierbare Möglichkeit, die PowerPoint-zu-PDF-Konvertierung in Ihren Anwendungen durchzuführen.

## Häufig gestellte Fragen

### F1: Kann Aspose.Slides für .NET große Präsentationen verarbeiten?
Ja, Aspose.Slides für .NET ist für die effiziente Verarbeitung von Präsentationen jeder Größe konzipiert.

### F2: Wie erhalte ich eine kostenlose Testversion von Aspose.Slides für .NET?
 Sie können eine kostenlose Testversion herunterladen unter[Hier](https://releases.aspose.com/).

### F3: Gibt es andere PDF-Exportoptionen?
 Ja, Sie können Schriftarten, Seitenlayout, Komprimierung und mehr anpassen mit dem`PdfOptions` Klasse.

### F4: Kann ich nur bestimmte Folien exportieren?
 Auf jeden Fall! Sie können bestimmte Folien auswählen, indem Sie`Slides` Sammlung im`Presentation` Klasse.

### F5: Wo finde ich weitere Beispiele?
 Besuchen Sie die[Aspose.Slides für .NET-Dokumentation](https://reference.aspose.com/slides/net/)für weitere Beispiele und Anwendungsfälle.