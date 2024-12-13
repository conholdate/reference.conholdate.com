---
title: Erstellungszeit von Thread-Kommentaren mit Aspose.Cells lesen
linktitle: Erstellungszeit von Thread-Kommentaren mit Aspose.Cells lesen
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Cells für .NET ganz einfach die Erstellungszeit von Thread-Kommentaren in einem Excel-Arbeitsblatt lesen können. Folgen Sie unserer ausführlichen Anleitung mit Schritt-für-Schritt-Anweisungen.
type: docs
weight: 21
url: /de/net/tutorials/cells/guide-worksheet-operations/read-created-time-of-threaded-comment/
---
## Einführung

Beim Arbeiten mit Excel-Dateien kann die Verwaltung von Kommentaren für die Zusammenarbeit und die Nachverfolgung von Feedback von entscheidender Bedeutung sein. In diesem Handbuch führen wir Sie durch den Prozess zum Lesen der Erstellungszeit von Thread-Kommentaren in einem Excel-Arbeitsblatt mithilfe von Aspose.Cells für .NET. Dieses leistungsstarke Tool bietet eine effiziente Möglichkeit zur Interaktion mit Excel-Dateien und ermöglicht es Entwicklern, detaillierte Informationen aus Kommentaren zu extrahieren, was insbesondere für die Nachverfolgung des Zeitpunkts von Feedback in kollaborativen Szenarien nützlich ist.

## Voraussetzungen

Bevor wir beginnen, müssen Sie sicherstellen, dass Ihre Entwicklungsumgebung für die Verwendung von Aspose.Cells für .NET richtig eingerichtet ist. Folgendes benötigen Sie:

1.  Aspose.Cells für .NET: Sie müssen die Aspose.Cells-Bibliothek installiert haben. Sie erhalten die neueste Version von[Aspose-Website](https://releases.aspose.com/cells/net/).
2. IDE: Visual Studio (oder eine beliebige .NET-IDE Ihrer Wahl) zum Schreiben und Ausführen Ihres Codes.
3. Grundlegende C#-Kenntnisse: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie den Beispielen leichter folgen.
4.  Excel-Datei: Für dieses Tutorial verwenden wir eine Excel-Datei namens`ThreadedCommentsSample.xlsx`, die einige Thread-Kommentare enthält. Stellen Sie sicher, dass Ihre Datei Kommentare enthält, die Sie nachvollziehen können.

## Importieren der erforderlichen Pakete

Zunächst müssen Sie die erforderlichen Namespaces für die Arbeit mit Aspose.Cells importieren. Öffnen Sie Ihr C#-Projekt und fügen Sie oben in Ihrer Codedatei die folgenden using-Direktiven hinzu:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

 Der`Aspose.Cells` Namespace ermöglicht den Zugriff auf alle Klassen und Methoden, die für die Bearbeitung von Excel-Dateien erforderlich sind, während`System` wird für allgemeine Funktionen wie Ausgabe und Ausnahmebehandlung benötigt.

## Schritt 1: Geben Sie das Verzeichnis der Excel-Datei an

Der erste Schritt besteht darin, den Pfad anzugeben, in dem Ihre Excel-Datei gespeichert ist. Dieser Pfad wird verwendet, um die Datei programmgesteuert zu finden.

```csharp
// Definieren Sie das Verzeichnis der Excel-Datei
string sourceDir = "Your Document Directory";
```

 Ersetzen`"C:\\YourDirectory\\"`mit dem tatsächlichen Pfad zu Ihrer Datei. Dadurch wird sichergestellt, dass das Programm weiß, wo sich die`ThreadedCommentsSample.xlsx`.

## Schritt 2: Laden Sie die Arbeitsmappe

 Nachdem das Verzeichnis festgelegt wurde, können wir nun die Excel-Arbeitsmappe laden. Dies geschieht durch die Erstellung eines neuen`Workbook` Objekt und Übergabe des Dateipfads daran.

```csharp
// Laden der Excel-Arbeitsmappe
Workbook workbook = new Workbook(sourceDir + "ThreadedCommentsSample.xlsx");
```

Wenn die Datei im angegebenen Pfad nicht gefunden wird, wird eine Ausnahme ausgelöst. Stellen Sie daher sicher, dass der Dateipfad korrekt ist, bevor Sie fortfahren.

## Schritt 3: Zugriff auf das gewünschte Arbeitsblatt

Sobald die Arbeitsmappe geladen ist, müssen Sie auf das Arbeitsblatt zugreifen, das die Thread-Kommentare enthält. In diesem Beispiel rufen wir das erste Arbeitsblatt der Arbeitsmappe ab.

```csharp
// Greifen Sie auf das erste Arbeitsblatt in der Arbeitsmappe zu
Worksheet worksheet = workbook.Worksheets[0];
```

 Wenn sich Ihre Kommentare in einem anderen Arbeitsblatt befinden, ändern Sie einfach den Index entsprechend. Verwenden Sie beispielsweise`Worksheets[1]` für das zweite Arbeitsblatt und so weiter.

## Schritt 4: Thread-Kommentare abrufen

Um die Thread-Kommentare abzurufen, müssen Sie die Zelle angeben, die die Kommentare enthält. In diesem Fall konzentrieren wir uns auf die Zelle`A1` Die Methode`GetThreadedComments` wird verwendet, um alle Kommentare abzurufen, die einer bestimmten Zelle zugeordnet sind.

```csharp
// Thread-Kommentare aus Zelle A1 abrufen
ThreadedCommentCollection threadedComments = worksheet.Comments.GetThreadedComments("A1");
```

Dadurch wird eine Sammlung von Thread-Kommentaren für Zelle A1 zurückgegeben. Wenn in der angegebenen Zelle keine Kommentare vorhanden sind, ist die Sammlung leer.

## Schritt 5: Durch die Kommentare iterieren und Erstellungszeit extrahieren

 Nachdem die Thread-Kommentare abgerufen wurden, besteht der nächste Schritt darin, die Sammlung zu durchlaufen und relevante Details zu extrahieren, einschließlich der Erstellungszeit für jeden Kommentar. Dies können wir ganz einfach erreichen, indem wir die`ThreadedCommentCollection`.

```csharp
// Durchlaufen Sie jeden Threadkommentar und zeigen Sie die Details an
foreach (ThreadedComment comment in threadedComments)
{
    Console.WriteLine("Comment: " + comment.Notes);
    Console.WriteLine("Author: " + comment.Author.Name);
    Console.WriteLine("Created Time: " + comment.CreatedTime);
}
```

 Dieser Code gibt den Inhalt des Kommentars, den Namen des Autors und den Zeitpunkt der Erstellung des Kommentars aus.`CreatedTime` Die Eigenschaft gibt den Zeitstempel zurück, als der Kommentar ursprünglich erstellt wurde.

## Schritt 6: Eine Bestätigungsnachricht anzeigen

Nachdem Sie die Thread-Kommentare erfolgreich gelesen und die Informationen angezeigt haben, empfiehlt es sich immer, eine Bestätigungsnachricht in Ihren Code einzufügen. Dadurch wird bestätigt, dass der Vorgang korrekt ausgeführt wurde.

```csharp
// Bestätigungsnachricht
Console.WriteLine("Successfully retrieved threaded comment created times.");
```

Diese Meldung wird nach Abschluss der Codeausführung auf der Konsole ausgegeben und bestätigt, dass der Vorgang ohne Fehler ausgeführt wurde.

## Abschluss

Sie haben nun gelernt, wie Sie mit Aspose.Cells für .NET ganz einfach die Erstellungszeit von Thread-Kommentaren in einem Excel-Arbeitsblatt lesen können. Diese Funktion ist für die Nachverfolgung von Kommentaren und Feedback in kollaborativen Umgebungen von unschätzbarem Wert und bietet wichtige Zeitstempel für Dokumentüberprüfungsprozesse. Wenn Sie dieser Anleitung folgen, können Sie Kommentardaten effizient extrahieren und in Ihren .NET-Anwendungen verwenden, Ihren Workflow verbessern und die Zusammenarbeit mit Teammitgliedern verbessern.

## Häufig gestellte Fragen

### Was ist Aspose.Cells für .NET?

Aspose.Cells für .NET ist eine umfassende Bibliothek, mit der Entwickler Excel-Dateien in .NET-Anwendungen erstellen, bearbeiten und verwalten können. Sie bietet robuste Tools zum programmgesteuerten Lesen, Schreiben und Ändern von Excel-Dateien.

### Wie kann ich Aspose.Cells für .NET herunterladen?

 Sie können die neueste Version von Aspose.Cells für .NET herunterladen von der[Aspose-Website](https://releases.aspose.com/cells/net/).

### Gibt es eine kostenlose Testversion?

 Ja, Aspose bietet eine kostenlose Testversion für Aspose.Cells für .NET an. Sie können die Testversion von der[Seite zur kostenlosen Testversion](https://releases.aspose.com/).

### Kann ich auf Kommentare aus anderen Zellen zugreifen?

 Ja, Sie können auf Thread-Kommentare von jeder Zelle im Arbeitsblatt aus zugreifen, indem Sie den Zellbezug im`GetThreadedComments` Methode. Ändern Sie einfach`"A1"` zur Referenz der gewünschten Zelle.

### Wo erhalte ich Support für Aspose.Cells?

 Wenn Sie Unterstützung benötigen oder Fragen haben, besuchen Sie die[Aspose-Forum](https://forum.aspose.com/c/cells/9), wo Sie Antworten finden oder die Community um Hilfe bitten können.