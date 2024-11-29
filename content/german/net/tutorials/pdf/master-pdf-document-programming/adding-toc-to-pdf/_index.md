---
title: Hinzufügen eines Inhaltsverzeichnisses zu einem PDF-Dokument
linktitle: Hinzufügen eines Inhaltsverzeichnisses zu einem PDF-Dokument
second_title: Aspose.PDF für .NET API-Referenz
description: Dieses Tutorial zeigt, wie Sie mit Aspose.Pdf für .NET einem PDF-Dokument ein Inhaltsverzeichnis (TOC) hinzufügen.
type: docs
weight: 40
url: /de/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Einführung

Das Erstellen eines Inhaltsverzeichnisses (TOC) in einem PDF-Dokument kann dessen Navigation und Zugänglichkeit erheblich verbessern. In dieser Anleitung zeigen wir, wie Sie mit Aspose.Pdf für .NET ein Inhaltsverzeichnis zu einer PDF-Datei hinzufügen.

## Voraussetzungen

Stellen Sie vor dem Start sicher, dass Sie über Folgendes verfügen:

1.   Aspose.PDF für .NET: Laden Sie die neueste Version herunter und installieren Sie sie von[Hier](https://releases.aspose.com/pdf/net/).
2.  Entwicklungsumgebung: Richten Sie eine .NET-Entwicklungsumgebung wie Visual Studio ein.
3.   Lizenz: Fordern Sie bei Bedarf eine temporäre Lizenz an; bitte besuchen Sie[Aspose.Pdf Lizenzierungsseite](https://asposepdf.com/developers) für weitere Informationen.

Erforderliche Bibliotheken importieren

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Schritt 1: Laden Sie das PDF-Dokument

Laden Sie Ihre vorhandene PDF-Datei dort hoch, wo Sie das Inhaltsverzeichnis einfügen möchten. Geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Schritt 2: Einfügen einer neuen Seite für das Inhaltsverzeichnis

Fügt am Anfang des PDF-Dokuments eine neue Seite ein. Diese Seite dient als Inhaltsverzeichnis (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Schritt 3: Erstellen eines TOC-Informationsobjekts

Erstellen Sie ein Objekt, das die Inhaltsverzeichnisinformationen darstellt. Fügen Sie einen Titel und einen Link hinzu, um die Navigation zu erleichtern.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Schritt 4: Inhaltsverzeichniselemente definieren

Definieren Sie die Elemente (oder Überschriften), die im Inhaltsverzeichnis angezeigt werden. Diese Elemente können den Lesern dabei helfen, zu bestimmten Abschnitten des Dokuments zu navigieren.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Schritt 5: Inhaltsverzeichnisüberschriften erstellen

Erstellen Sie Überschriften für die ersten beiden Elemente im Inhaltsverzeichnis. Diese Überschriften verlinken auf die entsprechenden Seiten.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Schritt 6: Speichern Sie das PDF mit dem Inhaltsverzeichnis

Speichern Sie abschließend die aktualisierte PDF-Datei.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Bestätigungsnachricht

Zeigen Sie eine Bestätigungsmeldung an, um den Benutzer darüber zu informieren, dass der Vorgang abgeschlossen ist.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Abschluss

Mit Aspose.PDF für .NET ist das Hinzufügen eines Inhaltsverzeichnisses zu einer PDF-Datei nicht nur einfach, sondern auch anpassbar. Egal, ob Sie einfache Navigationslinks oder komplexe Strukturen erstellen müssen, dieses Tool bietet alles. Vergessen Sie also nicht, beim nächsten Mal, wenn Sie an einer langen PDF-Datei arbeiten, ein Inhaltsverzeichnis für den professionellen Touch hinzuzufügen.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild des Inhaltsverzeichnisses in Aspose.PDF anpassen?

Ja, Sie können das Erscheinungsbild des Inhaltsverzeichnisses einschließlich Schriftart, -größe und -ausrichtung vollständig anpassen.

### Wie füge ich dem Inhaltsverzeichnis Unterüberschriften hinzu?

 Sie können Unterüberschriften hinzufügen, indem Sie die`Heading` Ebene (z. B.`Heading(2)`).

### Ist es möglich, das Inhaltsverzeichnis automatisch zu aktualisieren, wenn sich das Dokument ändert?

Nein, das Inhaltsverzeichnis wird nicht automatisch aktualisiert. Sie müssen es neu erstellen, wenn sich die Dokumentstruktur ändert.

### Kann ich Inhaltsverzeichniseinträge mit externen Dokumenten verknüpfen?

Ja, Sie können Hyperlinks verwenden, um Inhaltsverzeichniseinträge mit externen PDFs oder URLs zu verknüpfen.

### Unterstützt Aspose.PDF mehrstufige Inhaltsverzeichnisse?

Ja, Aspose.PDF unterstützt mehrstufige Inhaltsverzeichnisse für komplexe Dokumente mit Unterabschnitten.
