---
title: Anwendungslink in PDF-Datei erstellen
linktitle: Anwendungslink in PDF-Datei erstellen
second_title: Aspose.PDF für .NET API-Referenz
description: Diese umfassende Anleitung führt Sie durch den Prozess des Hinzufügens interaktiver Anwendungslinks zu PDF-Dokumenten mit Aspose.PDF für .NET. Verbessern Sie die Benutzereinbindung, indem Sie eine schnelle Navigation zu bestimmten Anwendungen oder Dateien ermöglichen.
type: docs
weight: 20
url: /de/net/tutorials/pdf/mastering-links-and-actions/creating-application-link/
---
## Einführung

Die Benutzerinteraktion in PDF-Dokumenten kann durch interaktive Elemente wie Anwendungslinks verbessert werden. Diese Links ermöglichen es Benutzern, schnell zu bestimmten Anwendungen oder Dateien zu navigieren, was das Gesamterlebnis verbessert. In diesem Handbuch werden wir den Prozess zum Erstellen von Anwendungslinks in einem PDF mit Aspose.PDF für .NET durchgehen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. .NET Framework: Stellen Sie sicher, dass das .NET Framework auf Ihrem System installiert ist. Aspose.PDF für .NET ist mit verschiedenen Versionen kompatibel.
2. Aspose.PDF-Bibliothek: Installieren Sie die Aspose.PDF-Bibliothek. Sie können sie von der Website herunterladen oder über NuGet installieren:
```bash
Install-Package Aspose.PDF
```
3. Grundlegende C#-Kenntnisse: Kenntnisse in C# sind von Vorteil, da wir C#-Code schreiben werden.

## Importieren erforderlicher Pakete

Erstellen Sie eine neue Konsolenanwendung in Ihrer bevorzugten IDE (z. B. Visual Studio). Vergessen Sie nicht, die erforderlichen Namespaces zu importieren:

```csharp
using System.IO;
using System;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
```

## Schritt 1: Dokumentpfad festlegen

Legen Sie das Verzeichnis fest, in dem Ihre PDF-Dokumente gespeichert werden:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihren PDF-Dateien.

## Schritt 2: Öffnen Sie das PDF-Dokument

Laden Sie die PDF-Datei dort hoch, wo Sie den Bewerbungslink erstellen möchten:

```csharp
Document document = new Document(dataDir + "CreateApplicationLink.pdf");
```

## Schritt 3: Linkanmerkung erstellen

Erstellen Sie als nächstes eine Linkanmerkung auf der gewünschten Seite:

```csharp
Page page = document.Pages[1]; // Wählen Sie die erste Seite
LinkAnnotation link = new LinkAnnotation(page, new Aspose.Pdf.Rectangle(100, 100, 300, 300));
```

Dieses Rechteck definiert den anklickbaren Bereich des Links.

## Schritt 4: Linkfarbe festlegen

Passen Sie das Erscheinungsbild des Links an:

```csharp
link.Color = Aspose.Pdf.Color.FromRgb(System.Drawing.Color.Green);
```

## Schritt 5: Definieren Sie die Link-Aktion

Legen Sie die Aktion für den Link fest und geben Sie an, was passiert, wenn darauf geklickt wird:

```csharp
link.Action = new LaunchAction(document, dataDir + "CreateApplicationLink.pdf");
```

Sie können den Pfad nach Bedarf ändern, um eine Verknüpfung zu einer Anwendung oder einem anderen Dokument herzustellen.

## Schritt 6: Hinzufügen der Anmerkung zur Seite

Fügen Sie die Link-Anmerkung zur Anmerkungssammlung der Seite hinzu:

```csharp
page.Annotations.Add(link);
```

## Schritt 7: Speichern Sie das Dokument

Speichern Sie die Änderungen in einer neuen PDF-Datei:

```csharp
dataDir = dataDir + "CreateApplicationLink_out.pdf";
document.Save(dataDir);
```

## Schritt 8: Bestätigen Sie den Vorgang

Geben Sie Feedback zur erfolgreichen Operation:

```csharp
Console.WriteLine("\nApplication link created successfully.\nFile saved at " + dataDir);
```

## Abschluss

In nur wenigen einfachen Schritten haben Sie gelernt, wie Sie mit Aspose.PDF für .NET einen Anwendungslink in einer PDF-Datei erstellen. Mit dieser leistungsstarken Bibliothek können Sie PDF-Dokumente interaktiver und ansprechender gestalten und Benutzer zu wertvollen Informationen oder Anwendungen führen.

## Häufig gestellte Fragen

### Was ist Aspose.PDF für .NET?
Aspose.PDF für .NET ist eine robuste Bibliothek zum Erstellen und Bearbeiten von PDF-Dateien innerhalb von .NET-Anwendungen.

### Wie kann ich Aspose.PDF herunterladen?
 Sie können Aspose.PDF für .NET herunterladen von[die Website](https://releases.aspose.com/pdf/net/).

### Gibt es eine kostenlose Testversion?
 Ja, Sie können auf eine kostenlose Testversion von Aspose.PDF zugreifen[Hier](https://releases.aspose.com/).

### Wo erhalte ich Support für Aspose.PDF?
 Für Unterstützung besuchen Sie die[Aspose PDF Support Forum](https://forum.aspose.com/c/pdf/10).

### Wie kann ich eine temporäre Lizenz für Aspose erhalten?
 Sie können eine temporäre Lizenz anfordern bei[diese Seite](https://purchase.aspose.com/temporary-license/).