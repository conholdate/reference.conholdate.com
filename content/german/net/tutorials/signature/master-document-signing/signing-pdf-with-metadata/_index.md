---
title: Anleitung zum Signieren von PDFs mit Metadaten unter Verwendung von GroupDocs.Signature
linktitle: Leitfaden zum Signieren von PDFs mit Metadaten
second_title: GroupDocs.Signature .NET API
description: Erfahren Sie, wie Sie Ihre PDF-Dokumente sicherer und nachverfolgbarer machen, indem Sie sie mit Metadaten unter Verwendung von GroupDocs.Signature für .NET signieren. Dieses umfassende Tutorial bietet eine klare Anleitung.
type: docs
weight: 11
url: /de/net/tutorials/signature/master-document-signing/signing-pdf-with-metadata/
---
## Einführung

In diesem Tutorial erfahren Sie, wie Sie ein PDF-Dokument signieren und Metadaten mit GroupDocs.Signature für .NET hinzufügen. Das Hinzufügen von Metadaten verbessert das Dokument, indem es wichtige Informationen wie Autorschaft, Erstellungsdatum, Dokument-ID und mehr bereitstellt.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  GroupDocs.Signature für .NET: Laden Sie es herunter von[Hier](https://releases.groupdocs.com/signature/net/).
2. Ein PDF-Dokument: Halten Sie eine Beispiel-PDF-Datei zur Unterschrift bereit.
3. Grundkenntnisse der C#-Programmierung: Zum Verständnis der Codebeispiele sind Kenntnisse der C#-Syntax erforderlich.

## Namespaces importieren

Beginnen Sie mit dem Importieren der erforderlichen Namespaces, um auf die notwendigen Klassen und Methoden zuzugreifen:

```csharp
using System;
using System.IO;
using GroupDocs.Signature;
using GroupDocs.Signature.Domain;
using GroupDocs.Signature.Options;
```

## Schritt 1: Laden Sie das PDF-Dokument

Geben Sie den Pfad des PDF-Dokuments an, das Sie signieren möchten:

```csharp
string filePath = "sample.pdf";
```

## Schritt 2: Ausgabedateipfad angeben

Legen Sie fest, wo das signierte PDF mit Metadaten gespeichert werden soll:

```csharp
string outputFilePath = Path.Combine("Your Document Directory", "SignPdfWithMetadata", "SignedWithMetadata.pdf");
```

## Schritt 3: Erstellen einer Signaturinstanz

 Initialisieren Sie einen`Signature` Instanz mit dem Pfad zum PDF-Dokument:

```csharp
using (Signature signature = new Signature(filePath))
{
    // Der Signatur-bezogene Code wird hier eingefügt.
}
```

## Schritt 4: Metadatenoptionen definieren

 Erstellen`MetadataSignOptions` und fügen Sie die Metadatenfelder zusammen mit ihren Werten hinzu:

```csharp
MetadataSignOptions options = new MetadataSignOptions();
options
    .Add(new PdfMetadataSignature("Author", "Mr. Sherlock Holmes")) // Zeichenfolgenwert
    .Add(new PdfMetadataSignature("CreatedOn", DateTime.Now))       // DateTime-Wert
    .Add(new PdfMetadataSignature("DocumentId", 123456))            // Ganzzahliger Wert
    .Add(new PdfMetadataSignature("SignatureId", 123.456D))         // Doppelter Wert
    .Add(new PdfMetadataSignature("Amount", 123.456M))              // Dezimalwert
    .Add(new PdfMetadataSignature("Total", 123.456F));              // Gleitkommawert
```

## Schritt 5: Unterschreiben Sie das Dokument

Signieren Sie das PDF-Dokument mit den angegebenen Metadatenoptionen und speichern Sie das signierte Dokument:

```csharp
SignResult result = signature.Sign(outputFilePath, options);
Console.WriteLine($"\nSource document signed successfully with {result.Succeeded.Count} signature(s).\nFile saved at {outputFilePath}.");
```

## Abschluss

In diesem Tutorial haben wir erläutert, wie Sie mithilfe von GroupDocs.Signature für .NET ein PDF-Dokument mit Metadaten signieren. Indem Sie diese Schritte befolgen, können Sie Ihre PDF-Dateien ganz einfach mit wertvollen Metadaten anreichern und so ihre Nachverfolgbarkeit und Nützlichkeit verbessern.

## Häufig gestellte Fragen

### Kann ich meinen PDF-Dokumenten benutzerdefinierte Metadatenfelder hinzufügen?

Ja, Sie können benutzerdefinierte Metadatenfelder hinzufügen, indem Sie den Feldnamen und den entsprechenden Wert mit GroupDocs.Signature für .NET angeben.

### Ist GroupDocs.Signature für .NET mit allen Versionen des .NET Frameworks kompatibel?

GroupDocs.Signature für .NET ist mit verschiedenen Versionen des .NET Frameworks kompatibel und gewährleistet so Flexibilität und einfache Integration.

### Unterstützt GroupDocs.Signature das Signieren anderer Dokumentformate außer PDF?

Ja, GroupDocs.Signature unterstützt eine breite Palette von Dokumentformaten, darunter Word, Excel, PowerPoint und mehr.

### Kann ich mit GroupDocs.Signature für .NET mehrere Dokumente gleichzeitig signieren?

Auf jeden Fall! Sie können mehrere Dokumente gleichzeitig signieren, indem Sie eine Liste von Dateien durchgehen und den Signaturprozess programmgesteuert anwenden.

### Gibt es technischen Support für GroupDocs.Signature-Benutzer?

Ja, GroupDocs bietet dedizierten technischen Support über seine Foren. Sie können auf das Support-Forum zugreifen[Hier](https://forum.groupdocs.com/c/signature/13).