---
title: Text aus mit Lesezeichen versehenen Abschnitten in Word-Dokumenten anhängen
linktitle: Text aus mit Lesezeichen versehenen Abschnitten in Word-Dokumenten anhängen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET nahtlos Text aus mit Lesezeichen versehenen Abschnitten eines Word-Dokuments anhängen. Dieses Schritt-für-Schritt-Tutorial.
type: docs
weight: 10
url: /de/net/tutorials/words/mastering-bookmarks/append-text-from-bookmarked-sections/
---
## Einführung

Fanden Sie es schon einmal schwierig, Text aus einem mit Lesezeichen versehenen Abschnitt in einem Word-Dokument anzuhängen? Dann sind Sie hier richtig! Dieses Tutorial führt Sie Schritt für Schritt durch den Vorgang mit Aspose.Words für .NET. Am Ende können Sie mit Lesezeichen versehenen Text wie ein Profi anhängen. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

-  Aspose.Words für .NET: Wenn Sie es noch nicht installiert haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Eine .NET-Entwicklungsumgebung wie Visual Studio.
- Grundkenntnisse in C#: Vertrautheit mit grundlegenden C#-Programmierkonzepten ist von Vorteil.
- Word-Dokument mit Lesezeichen: Ein Word-Dokument mit Lesezeichen, aus denen wir Text anhängen.

## Erforderliche Namespaces importieren

Zuerst müssen wir die erforderlichen Namespaces importieren, um auf die Aspose.Words-Funktionen zuzugreifen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Importing;
```

## Schritt 1: Laden Sie das Dokument und initialisieren Sie die Variablen

Beginnen wir mit dem Laden unserer Quell- und Ziel-Word-Dokumente und dem Initialisieren der erforderlichen Variablen.

```csharp
// Laden Sie die Quell- und Zieldokumente.
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");

// Initialisieren Sie den Dokumentimporter.
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);

// Suchen Sie das Lesezeichen im Quelldokument.
Bookmark srcBookmark = srcDoc.Range.Bookmarks["YourBookmarkName"];
```

## Schritt 2: Identifizieren Sie die Anfangs- und Endabsätze

Als nächstes müssen wir die Absätze lokalisieren, in denen das Lesezeichen beginnt und endet. Dies ist wichtig, um den richtigen Text zu extrahieren.

```csharp
// Identifizieren Sie die Absätze am Anfang und Ende des Lesezeichens.
Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

// Bestätigen Sie die Absätze.
if (startPara == null || endPara == null)
    throw new InvalidOperationException("Bookmark start or end does not have a valid paragraph parent.");
```

## Schritt 3: Überprüfen Sie die übergeordneten Absätze

Wir müssen sicherstellen, dass sowohl der Anfangs- als auch der Endabsatz denselben übergeordneten Knoten haben. Dies ist ein vereinfachter Ansatz, um Komplikationen zu vermeiden.

```csharp
// Überprüfen Sie, ob Anfangs- und Endabsatz denselben übergeordneten Absatz haben.
if (startPara.ParentNode != endPara.ParentNode)
    throw new InvalidOperationException("Start and end paragraphs must have the same parent.");
```

## Schritt 4: Identifizieren des zu stoppenden Knotens

Nun müssen wir festlegen, wo das Kopieren des Textes aufhören soll. Dies wird der Knoten unmittelbar nach dem letzten Absatz sein.

```csharp
// Identifizieren Sie den Knoten unmittelbar nach dem Endabsatz.
Node endNode = endPara.NextSibling;
```

## Schritt 5: Mit Lesezeichen versehenen Text an das Zieldokument anhängen

Abschließend durchlaufen wir die Knoten vom Startabsatz bis zum Knoten nach dem Endabsatz und hängen sie an das Zieldokument an.

```csharp
for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
{
    // Importieren Sie den aktuellen Knoten in das Zieldokument.
    Node newNode = importer.ImportNode(curNode, true);

    // Hängen Sie den importierten Knoten an das Zieldokument an.
    dstDoc.FirstSection.Body.AppendChild(newNode);
}

// Speichern Sie das aktualisierte Zieldokument.
dstDoc.Save("appended_document.docx");
```

## Abschluss

Herzlichen Glückwunsch! Sie haben mithilfe von Aspose.Words für .NET erfolgreich Text aus einem mit Lesezeichen versehenen Abschnitt in einem Word-Dokument angehängt. Diese leistungsstarke Bibliothek vereinfacht die Dokumentbearbeitung und Sie verfügen nun über eine weitere nützliche Fähigkeit in Ihrem Toolkit. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich Text aus mehreren Lesezeichen gleichzeitig anhängen?
Ja, Sie können den Vorgang für jedes Lesezeichen wiederholen und den Text nach Bedarf anhängen.

### Was passiert, wenn Anfangs- und Endabsatz unterschiedliche übergeordnete Elemente haben?
Im aktuellen Beispiel wird davon ausgegangen, dass sie denselben übergeordneten Knoten haben. Ist dies nicht der Fall, müssen Sie eine komplexere Handhabung implementieren.

### Bleibt die ursprüngliche Formatierung des angehängten Textes erhalten?
 Auf jeden Fall! Mit`ImportFormatMode.KeepSourceFormatting` stellt sicher, dass die ursprüngliche Formatierung erhalten bleibt.

### Ist es möglich, Text an einer bestimmten Stelle im Zieldokument anzuhängen?
Ja, Sie können Text an jeder gewünschten Position anhängen, indem Sie zum entsprechenden Knoten im Zieldokument navigieren.

### Kann ich Text aus einem Lesezeichen an einen neuen Abschnitt anhängen?
Ja, Sie können im Zieldokument einen neuen Abschnitt erstellen und den Text dort anhängen.