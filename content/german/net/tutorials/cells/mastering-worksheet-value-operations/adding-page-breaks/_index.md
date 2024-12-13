---
title: Hinzufügen von Seitenumbrüchen im Arbeitsblatt mit Aspose.Cells
linktitle: Hinzufügen von Seitenumbrüchen im Arbeitsblatt mit Aspose.Cells
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Entdecken Sie, wie Sie Ihre Excel-Arbeitsblätter verbessern können, indem Sie mithilfe von Aspose.Cells für .NET effektiv horizontale und vertikale Seitenumbrüche hinzufügen. Diese umfassende Anleitung führt Sie durch die erforderlichen Einrichtungs- und Codierungsschritte.
type: docs
weight: 10
url: /de/net/tutorials/cells/mastering-worksheet-value-operations/adding-page-breaks/
---
## Einführung

In diesem Tutorial zeigen wir Ihnen, wie Sie mithilfe von Aspose.Cells für .NET sowohl horizontale als auch vertikale Seitenumbrüche zu Ihren Excel-Arbeitsblättern hinzufügen. Am Ende sind Sie in der Lage, diese Techniken nahtlos in Ihre Projekte zu implementieren. Legen wir los!

## Voraussetzungen
Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass Sie Folgendes bereit haben:
- Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem System installiert ist.
-  Aspose.Cells für .NET: Laden Sie die Aspose.Cells-Bibliothek herunter und installieren Sie sie. Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/cells/net/).
- .NET Framework: Dieses Tutorial setzt voraus, dass Sie .NET Framework oder .NET Core verwenden. Der Vorgang kann in anderen Umgebungen leicht abweichen.
- Grundlegende C#-Kenntnisse: Vertrautheit mit der C#-Programmierung und dem Konzept von Seitenumbrüchen in Excel ist hilfreich.

## Pakete importieren
Um mit Aspose.Cells zu arbeiten, importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Nachdem Sie diese Namespaces importiert haben, können Sie mit der Interaktion mit Excel-Dateien beginnen und Änderungen, einschließlich Seitenumbrüchen, anwenden.

## Schritt 1: Richten Sie Ihre Arbeitsmappe ein
 Erstellen Sie eine neue Arbeitsmappe mit dem`Workbook` Klasse, die als Grundlage für die Bearbeitung von Excel-Dateien dient.

```csharp
// Geben Sie den Pfad zum Verzeichnis an, in dem Ihre Datei gespeichert wird
string dataDir = "Your Document Directory";
// Erstellen eines neuen Workbook-Objekts
Workbook workbook = new Workbook();
```
In diesem Code:
- `dataDir` gibt den Speicherort für Ihre Datei an.
-  Der`Workbook` Das Objekt wird instanziiert und ist bereit für Änderungen.

## Schritt 2: Einen horizontalen Seitenumbruch hinzufügen
Um einen horizontalen Seitenumbruch hinzuzufügen, der das Arbeitsblatt vertikal in zwei Teile teilt, verwenden Sie den folgenden Code:

```csharp
// Fügen Sie in Zeile 30 einen horizontalen Seitenumbruch hinzu
workbook.Worksheets[0].HorizontalPageBreaks.Add("Y30");
```
 Hier,`Worksheets[0]` bezieht sich auf das erste Blatt der Arbeitsmappe und`HorizontalPageBreaks.Add("Y30")` fügt in Zeile 30 einen Umbruch hinzu, sodass der Inhalt darüber auf einer Seite erscheint und der Inhalt darunter auf einer neuen Seite beginnt.

## Schritt 3: Einen vertikalen Seitenumbruch hinzufügen
Als Nächstes können Sie einen vertikalen Seitenumbruch hinzufügen, um den Inhalt horizontal über mehrere Spalten hinweg zu trennen:

```csharp
// Fügen Sie in Spalte Y einen vertikalen Seitenumbruch hinzu
workbook.Worksheets[0].VerticalPageBreaks.Add("Y30");
```
 In diesem Beispiel`VerticalPageBreaks.Add("Y30")`Erstellt einen Umbruch nach Spalte X und stellt so sicher, dass der Inhalt auf der linken Seite auf der einen Seite und der Inhalt auf der rechten Seite auf der anderen Seite erscheint.

## Schritt 4: Speichern der Arbeitsmappe
Speichern Sie abschließend die Arbeitsmappe, um die Änderungen beizubehalten:

```csharp
// Speichern Sie die Excel-Datei
workbook.Save(dataDir + "AddingPageBreaks_out.xls");
```
Diese Zeile speichert die Arbeitsmappe mit den hinzugefügten Seitenumbrüchen im angegebenen Pfad (`AddingPageBreaks_out.xls`).

## Abschluss
Das Hinzufügen von Seitenumbrüchen in Excel ist für die Verwaltung großer Datensätze und die Vorbereitung von Dokumenten für den Druck unerlässlich. Mit Aspose.Cells für .NET können Sie das Einfügen horizontaler und vertikaler Seitenumbrüche automatisieren, sodass Ihre Dokumente übersichtlicher und leichter lesbar werden.

## Häufig gestellte Fragen

### Wie füge ich in Aspose.Cells für .NET mehrere Seitenumbrüche hinzu?
 Sie können mehrere Seitenumbrüche einfügen, indem Sie den`HorizontalPageBreaks.Add()` oder`VerticalPageBreaks.Add()` Methoden mehrmals mit unterschiedlichen Zellbezügen.

### Kann ich einem bestimmten Arbeitsblatt in einer Arbeitsmappe Seitenumbrüche hinzufügen?
 Ja, geben Sie das Arbeitsblatt an mit dem`Worksheets[index]` Eigentum, wo`index` ist der nullbasierte Index des gewünschten Arbeitsblatts.

### Wie entferne ich einen Seitenumbruch in Aspose.Cells für .NET?
Entfernen Sie einen Seitenumbruch mit`HorizontalPageBreaks.RemoveAt()` oder`VerticalPageBreaks.RemoveAt()` indem Sie den Index des Seitenumbruchs angeben, den Sie löschen möchten.

### Kann ich automatisch Seitenumbrüche basierend auf der Inhaltsgröße hinzufügen?
Aspose.Cells bietet hierfür keine automatische Funktion, aber Sie können basierend auf der Zeilen-/Spaltenanzahl programmgesteuert berechnen, wo Umbrüche auftreten sollen.

### Kann ich Seitenumbrüche basierend auf einem bestimmten Zellbereich festlegen?
Ja, Sie können Seitenumbrüche für jede Zelle oder jeden Bereich festlegen, indem Sie den entsprechenden Zellbezug angeben, beispielsweise „A1“ oder „B15“.