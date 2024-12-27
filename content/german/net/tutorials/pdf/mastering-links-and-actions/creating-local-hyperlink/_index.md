---
title: Lokalen Hyperlink in PDF-Datei erstellen
linktitle: Lokalen Hyperlink in PDF-Datei erstellen
second_title: Aspose.PDF für .NET API-Referenz
description: Entdecken Sie, wie Sie die Navigation in Ihren PDF-Dokumenten verbessern können, indem Sie mit Aspose.PDF für .NET lokale Hyperlinks erstellen. Dieses Schritt-für-Schritt-Tutorial führt Sie durch den gesamten Prozess.
type: docs
weight: 40
url: /de/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Einführung

In dieser Anleitung führen wir Sie durch den Prozess der Erstellung lokaler Hyperlinks in einer PDF-Datei mit Aspose.PDF für .NET. Wir werden jeden Schritt klar aufschlüsseln, sodass Sie ihn auch dann mühelos befolgen können, wenn Sie noch keine Erfahrung mit der PDF-Bearbeitung haben.

## Voraussetzungen

Bevor Sie in den Code eintauchen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Visual Studio: Laden Sie es herunter von der[Visual Studio-Website](https://visualstudio.microsoft.com/).
2.  Aspose.PDF für .NET: Laden Sie die Bibliothek über das[Aspose-Website](https://releases.aspose.com/pdf/net/). Diese Bibliothek bietet zahlreiche Funktionen zur PDF-Bearbeitung.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind hilfreich, aber keine Sorge, wir erklären Ihnen den Code Zeile für Zeile.
4. .NET Framework: Stellen Sie sicher, dass das .NET Framework auf Ihrem Computer installiert ist. Überprüfen Sie die Anforderungen auf Aspose.PDF[Dokumentation](https://reference.aspose.com/pdf/net/).

Wenn diese Voraussetzungen erfüllt sind, können Sie lernen, wie Sie lokale Hyperlinks in Ihren PDF-Dokumenten erstellen!

## Importieren erforderlicher Pakete

Nachdem Sie nun alles eingerichtet haben, ist es an der Zeit, die erforderlichen Pakete in Ihr C#-Projekt zu importieren.

### Öffnen Sie Ihr Projekt

Öffnen Sie Ihr vorhandenes .NET-Projekt oder erstellen Sie ein neues in Visual Studio. Wenn Sie neu beginnen, wählen Sie auf dem Startbildschirm „Neues Projekt erstellen“ aus.

### Verweis auf Aspose.PDF hinzufügen

 Klicken Sie mit der rechten Maustaste auf "Abhängigkeiten" in Ihrem Projektordner im Solution Explorer. Wählen Sie "NuGet-Pakete verwalten" und suchen Sie nach`Aspose.PDF`, und installieren Sie die neueste verfügbare Version. Dadurch erhalten Sie alle Tools, die Sie zum Erstellen und Bearbeiten von PDFs benötigen.

### Namespaces importieren

Fügen Sie oben in Ihrer CS-Datei die folgenden Using-Direktiven hinzu:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Diese Anweisungen ermöglichen Ihnen einen nahtlosen Zugriff auf die Funktionen der Bibliothek.

Lassen Sie uns den Prozess der Erstellung lokaler Hyperlinks in einfache Schritte aufteilen.

## Schritt 1: Dokumentinstanz einrichten

 Erstellen Sie eine neue Instanz des`Document` Klasse, die die PDF-Datei darstellt, mit der Sie arbeiten werden.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Legen Sie Ihr Dokumentverzeichnis fest
Document doc = new Document(); // Dokumentinstanz erstellen
```

 Ersetzen`"YOUR_DOCUMENT_DIRECTORY"` durch den tatsächlichen Pfad auf Ihrem System, wo die PDF-Datei gespeichert wird.

## Schritt 2: Dem Dokument eine Seite hinzufügen

Fügen Sie als Nächstes Ihrem PDF-Dokument eine Seite hinzu.

```csharp
Page page = doc.Pages.Add(); // Neue Seite hinzufügen
```

Diese Zeile fügt dem Dokument eine neue Seite hinzu, auf der Ihr gesamter Inhalt platziert wird.

## Schritt 3: Erstellen Sie ein Textfragment

Lassen Sie uns nun einen Textabschnitt erstellen, der als anklickbarer Link fungiert.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Erstellen eines Textfragments
```

 Das`TextFragment` zeigt den Text an, auf den Benutzer klicken können.

## Schritt 4: Lokalen Hyperlink erstellen

Erstellen Sie jetzt einen lokalen Hyperlink, der auf Seite 7 verweist.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Erstellen eines lokalen Hyperlinks
link.TargetPageNumber = 7; // Legen Sie die Zielseite für den Link fest
text.Hyperlink = link; // Festlegen des Hyperlinks für das Textfragment
```

 Der`LocalHyperlink` Mit der Klasse können Sie die Zielseitenzahl für den Hyperlink angeben.

## Schritt 5: Fügen Sie das Textfragment zur Seite hinzu

Fügen Sie der von Ihnen erstellten Seite den anklickbaren Text hinzu.

```csharp
page.Paragraphs.Add(text); // Fügen Sie der Seite das Textfragment hinzu
```

Diese Zeile fügt Ihren Text zur Absatzsammlung der Seite hinzu.

## Schritt 6: Ein weiteres Textfragment erstellen (optional)

Fügen wir einen weiteren Hyperlink hinzu, um zurück zu Seite 1 zu navigieren.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Erstellen eines neuen Textfragments
textBack.IsInNewPage = true; // Geben Sie an, dass es auf einer neuen Seite erscheinen soll
```

## Schritt 7: Einrichten des zweiten lokalen Hyperlinks

Erstellen Sie einen weiteren lokalen Hyperlink für Seite 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Einen weiteren lokalen Hyperlink erstellen
linkBack.TargetPageNumber = 1; // Zielseite für den zweiten Hyperlink festlegen
textBack.Hyperlink = linkBack; // Setzen Sie den Hyperlink für das zweite Textfragment
```

## Schritt 8: Fügen Sie der neuen Seite das zweite Textfragment hinzu

Fügen Sie der Seite das zweite Textfragment hinzu.

```csharp
Page newPage = doc.Pages.Add(); // Fügen Sie für den zweiten Link eine neue Seite hinzu
newPage.Paragraphs.Add(textBack); // Fügen Sie das Textfragment zur neuen Seite hinzu
```

## Schritt 9: Speichern Sie das Dokument

Speichern Sie abschließend Ihr Dokument.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Geben Sie den Namen der Ausgabedatei an
doc.Save(dataDir); // Speichern des aktualisierten Dokuments
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Diese Zeile kombiniert Ihren Verzeichnispfad mit dem Dateinamen und dem`Save()` Methode speichert Ihr Dokument.

## Abschluss

Das Erstellen lokaler Hyperlinks in PDF-Dateien mit Aspose.PDF für .NET ist eine praktische Funktion, die die Navigation und das Benutzererlebnis verbessert. Sie verfügen jetzt über das Wissen, um Ihre Leser direkt zu den benötigten Informationen zu führen und Ihre PDFs interaktiver und benutzerfreundlicher zu gestalten.

## Häufig gestellte Fragen

### Was ist Aspose.PDF für .NET?
Aspose.PDF für .NET ist eine Bibliothek, die es Entwicklern ermöglicht, PDF-Dokumente programmgesteuert mithilfe des .NET-Frameworks zu erstellen, zu bearbeiten und zu konvertieren.

### Kann ich Hyperlinks zu externen Webseiten erstellen?
Ja, Aspose.PDF unterstützt neben lokalen Hyperlinks innerhalb der PDF auch das Erstellen von Hyperlinks zu externen URLs.

### Gibt es eine kostenlose Testversion für Aspose.PDF?
 Auf jeden Fall! Sie können die kostenlose Testversion über das[Aspose-Website](https://releases.aspose.com/).

### Welche Programmiersprachen unterstützt Aspose?
Aspose bietet Bibliotheken für verschiedene Programmiersprachen, darunter Java, C++, und Python, unter anderem.

### Wie erhalte ich Support für Aspose-Produkte?
 Sie erhalten Unterstützung über das[Aspose Forum](https://forum.aspose.com/c/pdf/10).