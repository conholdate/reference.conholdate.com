---
title: Festlegen der Anbieter-ID für digitale Signaturen im Word-Dokument
linktitle: Festlegen der Anbieter-ID für digitale Signaturen im Word-Dokument
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Ihren Word-Dokumenten mit einer bestimmten Signaturanbieter-ID sicher eine digitale Signatur hinzufügen.
type: docs
weight: 10
url: /de/net/tutorials/words/digital-signatures/set-digital-signature-provider-id/
---
## Einführung

Hallo! Wenn Sie Ihrem Word-Dokument eine digitale Signatur mit einer bestimmten Signaturanbieter-ID hinzufügen möchten, sind Sie hier richtig. Ob für rechtliche Vereinbarungen, Verträge oder andere wichtige Dokumente, eine sichere digitale Signatur ist unerlässlich. In diesem Tutorial führe ich Sie Schritt für Schritt durch den Prozess zum Festlegen einer Signaturanbieter-ID in einem Word-Dokument mit Aspose.Words für .NET. Lassen Sie uns anfangen!

## Voraussetzungen

Stellen Sie vor dem Eintauchen sicher, dass Sie Folgendes haben:

1. Aspose.Words für die .NET-Bibliothek:[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede C#-kompatible IDE.
3.  Word-Dokument: Ein Dokument mit einer Signaturzeile (z. B.`Signature line.docx`).
4.  Digitales Zertifikat: A`.pfx` Zertifikatsdatei (z. B.`morzal.pfx`).
5. Grundkenntnisse in C#: Vertrautheit mit grundlegenden C#-Konzepten ist hilfreich.

Und jetzt stürzen wir uns in die Action!

## Schritt 1: Erforderliche Namespaces importieren

Um zu beginnen, schließen Sie die erforderlichen Namespaces in Ihr Projekt ein. Dadurch können Sie auf die Aspose.Words-Bibliothek und zugehörige Klassen zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

## Schritt 2: Laden Sie Ihr Word-Dokument

Zuerst müssen Sie das Word-Dokument laden, das die Signaturzeile enthält. So geht's:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Ersetzen Sie unbedingt`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Ihr Dokument gespeichert ist.

## Schritt 3: Zugriff auf die Signaturzeile

Als nächstes greifen Sie auf die in Ihr Dokument eingebettete Signaturzeile zu. Die Signaturzeile wird als Formobjekt dargestellt:

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Dieser Code ruft die erste Form im Hauptteil des ersten Abschnitts ab und wandelt sie in eine`SignatureLine` Objekt.

## Schritt 4: Signaturoptionen einrichten

Erstellen wir nun die Signaturoptionen, die die Anbieter-ID und die Signaturzeilen-ID umfassen:

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Diese Optionen stellen sicher, dass beim Signieren die richtige Signaturanbieter-ID verwendet wird.

## Schritt 5: Laden Sie das digitale Zertifikat

 Um das Dokument digital zu signieren, müssen Sie Ihre`.pfx` Zertifikatsdatei:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "your_certificate_password");
```

 Ersetzen`"your_certificate_password"` durch das tatsächliche Passwort für Ihr Zertifikat (sofern vorhanden).

## Schritt 6: Unterschreiben Sie das Dokument

Jetzt können Sie das Dokument unterzeichnen. Verwenden Sie den folgenden Code, um den Signaturvorgang durchzuführen:

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Dadurch wird Ihr Dokument signiert und gespeichert als`Digitally signed.docx`.

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Words für .NET erfolgreich eine Signaturanbieter-ID in einem Word-Dokument festgelegt. Dieser Vorgang sichert nicht nur Ihre Dokumente, sondern stellt auch sicher, dass sie den Standards für digitale Signaturen entsprechen. Probieren Sie es gerne mit Ihren eigenen Dokumenten aus!

 Wenn Sie Fragen haben oder weitere Hilfe benötigen, sehen Sie sich die FAQs unten an oder besuchen Sie die[Aspose-Supportforum](https://forum.aspose.com/c/words/8).

## Häufig gestellte Fragen

### Was ist eine Signature Provider ID?

Eine Signaturanbieter-ID identifiziert den Anbieter der digitalen Signatur eindeutig und gewährleistet so Authentizität und Sicherheit.

### Kann ich zum Signieren eine beliebige PFX-Datei verwenden?

Ja, Sie können jedes gültige digitale Zertifikat verwenden. Stellen Sie einfach sicher, dass Sie das richtige Passwort haben, wenn es geschützt ist.

### Wie erhalte ich eine PFX-Datei?

Sie können eine PFX-Datei von einer Zertifizierungsstelle (CA) erhalten oder mit Tools wie OpenSSL eine solche erstellen.

### Ist es möglich, mehrere Dokumente gleichzeitig zu unterzeichnen?

Auf jeden Fall! Sie können mehrere Dokumente durchlaufen und den Signaturvorgang auf jedes einzelne anwenden.

### Was ist, wenn mein Dokument keine Signaturzeile hat?

Sie müssen zuerst eine Signaturzeile einfügen. Aspose.Words bietet Methoden zum programmgesteuerten Hinzufügen von Signaturzeilen.