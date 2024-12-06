---
title: Hinzufügen von Schaltflächenkomponenten mit GroupDocs.Annotation für .NET
linktitle: Hinzufügen von Schaltflächenkomponenten
second_title: GroupDocs.Annotation .NET API
description: Entdecken Sie, wie Sie Ihre PDF-Dokumente verbessern können, indem Sie mit GroupDocs.Annotation für .NET interaktive Schaltflächenkomponenten hinzufügen. Dieses Schritt-für-Schritt-Tutorial.
type: docs
weight: 10
url: /de/net/tutorials/annotation/guide-to-document-components/adding-button-component/
---
## Einführung

In diesem Tutorial führen wir Sie durch den unkomplizierten Prozess des Hinzufügens einer Schaltflächenkomponente zu einem PDF-Dokument mithilfe der GroupDocs.Annotation-Bibliothek für .NET. Am Ende dieses Leitfadens sind Sie in der Lage, Ihre PDF-Dokumente mit interaktiven Funktionen zu verbessern.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Folgendes vorhanden ist:

1.  GroupDocs.Annotation für .NET: Laden Sie die GroupDocs.Annotation für .NET-Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/annotation/net/).
2. Entwicklungsumgebung: Richten Sie eine geeignete Entwicklungsumgebung mit installiertem .NET-Framework ein.

## Schritt 1: Erforderliche Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using GroupDocs.Annotation.Models;
using GroupDocs.Annotation.Models.AnnotationModels;
using GroupDocs.Annotation.Models.FormatSpecificComponents.Pdf;
using GroupDocs.Annotation.Options;
```

## Schritt 2: Ausgabepfad initialisieren

Definieren Sie den Ausgabepfad, in dem die geänderte PDF-Datei gespeichert wird:

```csharp
string outputPath = Path.Combine("Your Document Directory", "result" + Path.GetExtension("input.pdf"));
```

## Schritt 3: Eine Schaltflächenkomponente hinzufügen

Lassen Sie uns nun die Schaltflächenkomponente erstellen und zu Ihrer PDF-Datei hinzufügen:

```csharp
using (Annotator annotator = new Annotator("input.pdf"))
{
    ButtonComponent button = new ButtonComponent
    {
        Box = new Rectangle(100, 100, 100, 100), // Position und Größe des Buttons
        PenColor = 65535,                       // Farbe des Schaltflächenrahmens
        Style = BorderStyle.Dashed,             // Rahmenstil
        BorderWidth = 0,                        // Rahmenbreite
        BorderColor = 0,                        // Rahmenfarbe
        AlternateName = "Name",                 // Alternativer Name für die Schaltfläche
        PartialName = "Partial Name",           // Teilname für die Schaltfläche
        NormalCaption = "Caption",               // Auf der Schaltfläche angezeigter Text
        ButtonColor = 16761035,                 // Hintergrundfarbe der Schaltfläche
        Replies = new List<Reply>
        {
            new Reply { Comment = "First comment", RepliedOn = DateTime.Now },
            new Reply { Comment = "Second comment", RepliedOn = DateTime.Now }
        }
    };

    annotator.Add(button); // Fügen Sie die Schaltfläche zum Annotator hinzu
    annotator.Save("result.pdf"); // Speichern Sie die geänderte PDF
}
```

## Schritt 4: Ausgabepfad anzeigen

Informieren Sie den Benutzer abschließend, wo die Ausgabedatei gespeichert ist:

```csharp
Console.WriteLine($"\nDocument saved successfully.\nCheck output in {outputPath}.");
```

Herzlichen Glückwunsch! Sie haben mit GroupDocs.Annotation für .NET erfolgreich eine Schaltflächenkomponente zu einem PDF-Dokument hinzugefügt.

## Abschluss

In diesem Tutorial haben wir gezeigt, wie Sie mit GroupDocs.Annotation für .NET Schaltflächenkomponenten in PDF-Dokumente integrieren. Wenn Sie diese Schritte befolgen, können Sie die Interaktivität Ihrer PDF-Dokumente erheblich verbessern.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild der Schaltfläche anpassen?

Auf jeden Fall! Sie können verschiedene Eigenschaften wie Größe, Farbe und Stil an Ihre Anforderungen anpassen.

### Ist GroupDocs.Annotation für .NET mit allen PDF-Versionen kompatibel?

Ja, GroupDocs.Annotation für .NET unterstützt eine breite Palette von PDF-Versionen und gewährleistet so die Kompatibilität mit den meisten Dokumenten.

### Kann ich einem einzelnen PDF-Dokument mehrere Schaltflächenkomponenten hinzufügen?

Ja, Sie können einem PDF-Dokument beliebig viele Schaltflächenkomponenten hinzufügen.

### Unterstützt GroupDocs.Annotation für .NET andere Dateiformate?

Ja, es unterstützt neben PDF verschiedene Dokumentformate, darunter DOCX, PPTX und XLSX.

### Gibt es eine Trial-Version zum Testen?

 Ja, Sie können auf eine kostenlose Testversion von GroupDocs.Annotation für .NET zugreifen von[Hier](https://releases.groupdocs.com/).
