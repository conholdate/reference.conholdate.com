---
title: Mit GroupDocs.Signature Textsignaturen zu Dokumenten hinzufügen
linktitle: Textsignaturen zu Dokumenten hinzufügen
second_title: GroupDocs.Signature .NET API
description: Erfahren Sie, wie Sie mit GroupDocs.Signature für .NET Dokumente mit Text signieren. Schritt-für-Schritt-Anleitung zum programmgesteuerten Hinzufügen von Textsignaturen.
type: docs
weight: 17
url: /de/net/tutorials/signature/master-advanced-sign-techniques/add-text-signatures-to-documents/
---
## Einführung

In der heutigen digitalen Landschaft ist die elektronische Signatur von Dokumenten unverzichtbar geworden, um Arbeitsabläufe zu optimieren und Ressourcen zu sparen. GroupDocs.Signature für .NET bietet eine leistungsstarke Lösung zum programmgesteuerten Hinzufügen von Textsignaturen zu verschiedenen Dokumentformaten. Dieses Tutorial führt Sie durch die Schritte zum Signieren eines Dokuments mit Text mithilfe von GroupDocs.Signature für .NET.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. GroupDocs.Signature für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von[Hier](https://releases.groupdocs.com/signature/net/).
2. Entwicklungsumgebung: Richten Sie Ihre .NET-Entwicklungsumgebung ein.
3. Dokument: Bereiten Sie das Dokument vor, das Sie unterzeichnen möchten (z. B. PDF, Word).

## Erforderliche Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr .NET-Projekt:

```csharp
using System;
using System.IO;
using System.Drawing;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Schritt 1: Dokument laden

Laden Sie zunächst das Dokument hoch, das Sie unterzeichnen möchten:

```csharp
string filePath = "sample.pdf"; // Pfad zu Ihrem Dokument
string fileName = Path.GetFileName(filePath);
```

## Schritt 2: Definieren Sie den Ausgabedateipfad

Legen Sie als Nächstes den Ausgabedateipfad fest, in dem das signierte Dokument gespeichert wird:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignWithText", fileName);
```

## Schritt 3: Signaturoptionen erstellen

Konfigurieren Sie die Optionen für Ihre Textsignatur, einschließlich Inhalt, Position, Größe, Farbe und Schriftstil:

```csharp
TextSignOptions options = new TextSignOptions("John Smith")
{
    Left = 50, // X-Position
    Top = 200, // Y-Position
    Width = 100, // Breite der Signatur
    Height = 30, // Höhe der Signatur
    ForeColor = Color.Red, // Textfarbe
    Font = new SignatureFont { Size = 14, FamilyName = "Comic Sans MS" } // Schriftarteinstellungen
};
```

## Schritt 4: Unterschreiben Sie das Dokument

Verwenden Sie abschließend GroupDocs.Signature, um die Textsignatur anzuwenden und das signierte Dokument zu speichern:

```csharp
using (Signature signature = new Signature(filePath))
{
    SignResult result = signature.Sign(outputFilePath, options); // Unterschreiben Sie das Dokument
    Console.WriteLine($"\nDocument signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
}
```

## Abschluss

In diesem Tutorial haben wir gezeigt, wie Sie mit GroupDocs.Signature für .NET programmgesteuert eine Textsignatur zu einem Dokument hinzufügen. Indem Sie diese Schritte befolgen, können Sie die Sicherheit und Authentizität Ihrer Dokumente effizient verbessern.

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild der Textsignatur anpassen?
Ja, Sie können verschiedene Attribute wie Farbe, Schriftart, Größe und Position der Textsignatur an Ihre Bedürfnisse anpassen.

### Ist GroupDocs.Signature mit mehreren Dokumentformaten kompatibel?
Auf jeden Fall! GroupDocs.Signature unterstützt eine Vielzahl von Formaten, darunter PDF, Word, Excel, PowerPoint und mehr.

### Kann ich einem einzelnen Dokument mehrere Textsignaturen hinzufügen?
Ja, Sie können mehrere Textsignaturen hinzufügen, jede mit eigenen Anpassungsoptionen.

### Stellt GroupDocs.Signature die Dokumentintegrität nach der Signierung sicher?
Ja, die Bibliothek verwendet robuste kryptografische Algorithmen, um die Dokumentintegrität sicherzustellen und Manipulationen nach der Signierung zu verhindern.

### Gibt es eine Testversion zum Ausprobieren vor dem Kauf?
 Ja, Sie können eine kostenlose Testversion herunterladen von[Hier](https://releases.groupdocs.com/) um die Funktionen zu erkunden, bevor Sie einen Kauf tätigen.