---
title: Lesezeichen mit benannten Zielen in PDFs aus Excel-Dateien hinzufügen
linktitle: Lesezeichen mit benannten Zielen in PDFs aus Excel-Dateien hinzufügen
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Cells für .NET ganz einfach interaktive PDFs aus Excel-Dateien erstellen. In diesem Tutorial erfahren Sie, wie Sie Lesezeichen mit benannten Zielen hinzufügen, um die PDF-Navigation zu verbessern.
type: docs
weight: 10
url: /de/net/tutorials/cells/mastering-rendering-and-exporting/add-bookmarks-with-named-destinations/
---
## Einführung

Das Navigieren in großen PDF-Dateien kann sich oft wie die Suche nach der Nadel im Heuhaufen anfühlen, insbesondere wenn sie aus umfangreichen Excel-Tabellen erstellt wurden. Lesezeichen in PDF-Dokumenten bieten eine nahtlose Möglichkeit, zwischen relevanten Abschnitten einer Datei zu springen und so das Benutzererlebnis zu verbessern. Diese ausführliche Anleitung führt Sie durch den Prozess des Hinzufügens von Lesezeichen mit benannten Zielen zu einer PDF-Datei, die mit Aspose.Cells für .NET aus einer Excel-Datei erstellt wurde.

## Voraussetzungen für die Arbeit mit Aspose.Cells für .NET

Bevor wir uns in den Code vertiefen, müssen Sie unbedingt sicherstellen, dass Sie alle Tools für eine erfolgreiche Implementierung eingerichtet haben. Hier sind die Voraussetzungen:

1. Visual Studio: Die empfohlene IDE für die .NET-Entwicklung. Stellen Sie sicher, dass es auf Ihrem System installiert und richtig konfiguriert ist.
2.  Aspose.Cells für .NET: Die Kernbibliothek, die für die programmgesteuerte Bearbeitung von Excel-Dateien erforderlich ist. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/cells/net/) Wenn Sie neu bei Aspose sind, können Sie mit dem beginnen[Kostenlose Testversion](https://releases.aspose.com/).
3. .NET Framework: Stellen Sie sicher, dass Sie eine kompatible Version des .NET Frameworks verwenden. Aspose.Cells unterstützt mehrere Versionen.
4. Grundlegende C#-Kenntnisse: Grundlegende Kenntnisse in C# sind hilfreich, um dem Code folgen zu können.

Wenn diese Komponenten vorhanden sind, können Sie mit der Erstellung von PDF-Dokumenten mit Lesezeichen beginnen!

## Einrichten Ihres Projekts

Sobald Ihre Entwicklungsumgebung bereit ist, können Sie mit der Erstellung eines neuen C#-Projekts in Visual Studio fortfahren. Um mit den Funktionen von Aspose.Cells arbeiten zu können, müssen Sie die erforderlichen Namespaces importieren.

## Importieren erforderlicher Namespaces

Fügen Sie oben in Ihrer C#-Datei Folgendes hinzu`using` Anweisungen, um sicherzustellen, dass Ihr Projekt auf Aspose.Cells für .NET zugreifen kann:

```csharp
using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Aspose.Cells.Rendering;
using System.Drawing.Imaging;
```

Diese Namespaces bieten Zugriff auf die wesentlichen Klassen, die Ihnen dabei helfen, Excel-Daten zu bearbeiten und in ein PDF zu konvertieren.

## Schritt 1: Verzeichnisse für Eingabe- und Ausgabedateien einrichten

Der erste Schritt besteht darin, die Eingabe- und Ausgabedateiverzeichnisse zu definieren. Dadurch wird sichergestellt, dass die Excel-Quelldatei und die resultierende PDF-Datei an den richtigen Stellen abgelegt werden.

```csharp
string sourceDir = "Your Document Directory";  // Pfad zu Ihren Excel-Dateien
string outputDir = "Your Document Directory"; // Pfad, in dem das Ausgabe-PDF gespeichert wird
```

Dies ist vergleichbar mit dem Organisieren Ihres Arbeitsbereichs vor dem Starten eines Projekts.

## Schritt 2: Laden der Excel-Arbeitsmappe

 Der nächste Schritt besteht darin, Ihre Excel-Quelldatei zu laden. Mit Aspose.Cells können Sie eine Excel-Datei ganz einfach in eine`Workbook` Objekt, das Zugriff auf alle seine Blätter, Zellen und Inhalte bietet.

```csharp
Workbook wb = new Workbook(sourceDir + "sampleExcelFile.xlsx");
```

Dadurch wird die Arbeitsmappe geöffnet und für die Bearbeitung vorbereitet. Sie können jetzt mit dem Extrahieren und Formatieren der Daten für das PDF beginnen.

## Schritt 3: Zugriff auf das Arbeitsblatt

Nachdem die Arbeitsmappe nun geladen ist, ist es an der Zeit, auf das Arbeitsblatt zuzugreifen, in dem sich die relevanten Zellen für Lesezeichen befinden. In diesem Beispiel arbeiten wir mit dem ersten Arbeitsblatt:

```csharp
Worksheet ws = wb.Worksheets[0]; // Zugriff auf das erste Arbeitsblatt
```

Dieser Schritt legt die Leinwand für Ihre Lesezeichen fest. Jede Zelle, auf die Sie für ein Lesezeichen verweisen, stammt aus diesem Arbeitsblatt.

## Schritt 4: Lesezeichen mit benannten Zielen erstellen

An diesem Punkt können wir mit dem Erstellen von Lesezeichen beginnen. Lesezeichen sind im Wesentlichen Links, die schnellen Zugriff auf bestimmte Bereiche Ihres Dokuments ermöglichen. In diesem Beispiel erstellen wir ein Lesezeichen für Zelle „C5“.

### Erstellen eines Lesezeichens für eine einzelne Zelle

 Um ein Lesezeichen zu erstellen, müssen Sie zunächst auf die Zelle zugreifen, zu der Sie eine Verknüpfung erstellen möchten. Anschließend erstellen Sie ein`PdfBookmarkEntry` und verknüpfen Sie es mit der Position der Zelle.

```csharp
Cell cell = ws.Cells["C5"];
PdfBookmarkEntry bookmarkEntry = new PdfBookmarkEntry();
bookmarkEntry.Text = "Bookmark for C5"; // Der Text für das Lesezeichen
bookmarkEntry.Destination = cell;  // Verknüpfen des Lesezeichens mit der Zelle
bookmarkEntry.DestinationName = "AsposeCells--" + cell.Name; // Eindeutiger Zielname
```

Stellen Sie sich das so vor, als ob Sie eine Stelle im Dokument markieren, zu der Sie mit einem einzigen Klick zurückkehren können. Sie können dem Lesezeichen einen beliebigen Text zuweisen (z. B. „Lesezeichen für C5“) und es mit einer bestimmten Zelle verknüpfen.

### Hinzufügen von Unterlesezeichen für eine verbesserte Navigation

Sie können die Benutzererfahrung verbessern, indem Sie Unterlesezeichen hinzufügen, die vom Hauptlesezeichen abzweigen. Diese Unterlesezeichen können auf verschiedene Bereiche innerhalb desselben Arbeitsblatts oder auf andere Blätter verweisen.

```csharp
cell = ws.Cells["G56"];
PdfBookmarkEntry subbookmarkEntry1 = new PdfBookmarkEntry();
subbookmarkEntry1.Text = "Sub-Bookmark 1"; // Text für das erste Unterlesezeichen
subbookmarkEntry1.Destination = cell;
subbookmarkEntry1.DestinationName = "AsposeCells--" + cell.Name;

cell = ws.Cells["L4"];
PdfBookmarkEntry subbookmarkEntry2 = new PdfBookmarkEntry();
subbookmarkEntry2.Text = "Sub-Bookmark 2"; // Text für das zweite Unterlesezeichen
subbookmarkEntry2.Destination = cell;
subbookmarkEntry2.DestinationName = "AsposeCells--" + cell.Name;
```

Diese Unterlesezeichen dienen als zusätzliche Wegweiser zum Navigieren durch das Dokument, ähnlich wie Kapitel in einem Buch.

### Gruppieren von Unterlesezeichen unter einem Hauptlesezeichen

Um eine hierarchische Struktur zu erstellen, können Sie diese Unterlesezeichen unter dem Hauptlesezeichen hinzufügen. Dies erleichtert Benutzern die Navigation zu verschiedenen Abschnitten.

```csharp
ArrayList list = new ArrayList();
list.Add(subbookmarkEntry1);
list.Add(subbookmarkEntry2);
bookmarkEntry.SubEntry = list; // Untergeordnete Lesezeichen zum Hauptlesezeichen hinzufügen
```

Dadurch wird eine baumartige Struktur erstellt, in der jedes Lesezeichen mehrere Unterlesezeichen haben kann.

## Schritt 5: PDF mit Lesezeichen speichern

### Festlegen von PDF-Speicheroptionen

 Bevor wir das Dokument als PDF speichern, müssen wir die Speicheroptionen angeben und sicherstellen, dass die Lesezeichen eingeschlossen werden. Wir verwenden`PdfSaveOptions` zu diesem Zweck.

```csharp
PdfSaveOptions opts = new PdfSaveOptions();
opts.Bookmark = bookmarkEntry;  // Zuweisen der Lesezeichen zum PDF
```

Dies weist Aspose.Cells an, ein PDF zu generieren, das die gerade erstellten Lesezeichen enthält.

### Speichern des Dokuments

Nachdem die Lesezeichen gesetzt sind, können wir die Arbeitsmappe als PDF speichern.

```csharp
wb.Save(outputDir + "outputWithBookmarks.pdf", opts);
```

Dadurch wird das endgültige PDF mit anklickbaren Lesezeichen erstellt, sodass Benutzer schnell zu bestimmten Abschnitten des Dokuments springen können.

## Abschluss

Indem Sie diese einfachen Schritte befolgen, haben Sie mit Aspose.Cells für .NET erfolgreich ein PDF mit Lesezeichen und benannten Zielen aus einer Excel-Datei erstellt. Die Möglichkeit, Lesezeichen hinzuzufügen, verbessert nicht nur das Benutzererlebnis, sondern macht auch die Navigation in großen Dokumenten viel effizienter. Egal, ob Sie an einem Bericht, einem Leitfaden oder einer Präsentation arbeiten, das Setzen von Lesezeichen für wichtige Abschnitte hilft Ihren Lesern, das Beste aus Ihrem Dokument herauszuholen.

## Häufig gestellte Fragen

### Was ist Aspose.Cells für .NET?
Aspose.Cells für .NET ist eine leistungsstarke API für die Arbeit mit Excel-Dateien, mit der Sie Excel-Dokumente programmgesteuert erstellen, bearbeiten und konvertieren können. Mit diesem Tool können Sie Daten, Diagramme und Formatierungen problemlos bearbeiten.

### Wie kann ich eine kostenlose Testversion von Aspose.Cells für .NET erhalten?
 Sie können eine kostenlose Testversion von Aspose.Cells für .NET herunterladen von[Hier](https://releases.aspose.com/).

### Mit welchen Dateiformaten kann Aspose.Cells arbeiten?
Aspose.Cells unterstützt eine Vielzahl von Dateiformaten, darunter XLSX, XLS, CSV, PDF und viele andere.

### Kann ich das Erstellen von Lesezeichen in PDF automatisieren?
Ja! Der Prozess kann vollständig automatisiert werden, indem Sie Aspose.Cells in Ihre Anwendungen integrieren, sodass Sie im Rahmen Ihres Workflows dynamisch Excel-basierte PDFs mit Lesezeichen generieren können.

### Wo erhalte ich Support für Aspose.Cells für .NET?
 Besuchen Sie die[Aspose-Foren](https://forum.aspose.com/c/cells/9) um Fragen zu stellen oder Probleme zu melden.