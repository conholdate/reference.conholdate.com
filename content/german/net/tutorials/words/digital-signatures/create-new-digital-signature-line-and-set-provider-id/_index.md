---
title: Neue digitale Signaturzeile erstellen und Provider-ID festlegen
linktitle: Neue digitale Signaturzeile erstellen und Provider-ID festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Entdecken Sie, wie Sie mit Aspose.Words für .NET programmgesteuert Signaturzeilen zu Ihren Word-Dokumenten hinzufügen. Dieser umfassende Leitfaden behandelt alles, vom Einrichten Ihrer Entwicklungsumgebung bis zum Einfügen von Signaturzeilen und dem sicheren Signieren von Dokumenten.
type: docs
weight: 10
url: /de/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Einführung

Hallo Technikbegeisterte! Wollten Sie schon immer die Einfügung von Signaturzeilen in Ihre Word-Dokumente automatisieren? Heute zeigen wir Ihnen, wie Sie dies mit Aspose.Words für .NET erreichen. Diese Schritt-für-Schritt-Anleitung führt Sie durch die Erstellung einer Signaturzeile und die Festlegung der Anbieter-ID, sodass Ihre Dokumentverarbeitungsaufgaben effizienter und reibungsloser werden.

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass Sie alles eingerichtet haben:

1.  Aspose.Words für .NET: Wenn Sie es noch nicht installiert haben, laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Verwenden Sie Visual Studio oder ein beliebiges C#-Entwicklungssetup.
3. .NET Framework: Stellen Sie sicher, dass das .NET Framework auf Ihrem Computer installiert ist.
4. PFX-Zertifikat: Zum Signieren von Dokumenten benötigen Sie ein PFX-Zertifikat, das Sie von einer vertrauenswürdigen Zertifizierungsstelle erhalten.

## Erforderliche Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Lassen Sie uns nun in die Details zum Erstellen einer neuen Signaturzeile und zum Festlegen der Anbieter-ID eintauchen.

## Schritt 1: Neues Dokument erstellen

Zuerst müssen wir ein neues Word-Dokument erstellen, das als Vorlage für unsere Signaturzeile dient:

```csharp
// Geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Hier initialisieren wir ein neues`Document` und ein`DocumentBuilder`, wodurch wir problemlos Elemente hinzufügen können.

## Schritt 2: Optionen für die Signaturzeile festlegen

Als Nächstes definieren wir die Optionen für unsere Signaturzeile, einschließlich Name, Titel, E-Mail und anderen relevanten Details des Unterzeichners:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Mithilfe dieser Optionen können Sie die Signaturzeile personalisieren und sie klar und professionell gestalten.

## Schritt 3: Einfügen der Signaturzeile

Nachdem wir unsere Optionen parat haben, können wir nun die Signaturzeile in das Dokument einfügen:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 Der`InsertSignatureLine`Methode fügt die Signaturzeile hinzu und wir weisen ihr eine eindeutige Provider-ID zu.

## Schritt 4: Speichern Sie das Dokument

Nachdem wir die Signaturzeile eingefügt haben, speichern wir das Dokument:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Dadurch wird Ihr Dokument mit der neu hinzugefügten Signaturzeile gespeichert.

## Schritt 5: Signaturoptionen einrichten

Nun konfigurieren wir die Signaturoptionen, einschließlich der Signaturzeilen-ID, der Anbieter-ID, Kommentare und der Signaturzeit:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Diese Einstellungen stellen sicher, dass das Dokument mit den richtigen Angaben signiert wird.

## Schritt 6: Zertifikatsinhaber anlegen

Um das Dokument zu signieren, müssen wir mithilfe des PFX-Zertifikats einen Zertifikatsinhaber erstellen:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Ersetzen`"morzal.pfx"` mit Ihrem tatsächlichen Zertifikatsdateinamen und`"aw"` mit Ihrem Zertifikatspasswort.

## Schritt 7: Unterschreiben Sie das Dokument

Zum Schluss unterzeichnen wir das Dokument mit dem Dienstprogramm für digitale Signaturen:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Durch diesen Vorgang wird das Dokument signiert und als neue Datei gespeichert.

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich eine Signaturzeile erstellt und die Anbieter-ID in einem Word-Dokument mit Aspose.Words für .NET festgelegt. Diese leistungsstarke Bibliothek vereinfacht die Dokumentverarbeitung und macht Ihren Workflow effizienter. Probieren Sie es aus und sehen Sie, wie es Ihre Projekte verbessern kann!

## Häufig gestellte Fragen

### Kann ich das Erscheinungsbild der Signaturzeile anpassen?
 Auf jeden Fall! Sie können verschiedene Optionen im`SignatureLineOptions` um zu Ihrem Stil und Ihren Anforderungen zu passen.

### Was ist, wenn ich kein PFX-Zertifikat habe?
Sie müssen eines von einer vertrauenswürdigen Zertifizierungsstelle beziehen, da es für die digitale Signatur von Dokumenten unerlässlich ist.

### Kann ich einem Dokument mehrere Signaturzeilen hinzufügen?
Ja, Sie können mehrere Signaturzeilen hinzufügen, indem Sie den Einfügevorgang mit unterschiedlichen Optionen wiederholen.

### Ist Aspose.Words für .NET mit .NET Core kompatibel?
Ja, Aspose.Words für .NET unterstützt .NET Core und ist daher vielseitig für verschiedene Entwicklungsumgebungen einsetzbar.

### Wie sicher sind die digitalen Signaturen?
Mit Aspose.Words erstellte digitale Signaturen sind hochsicher, sofern Sie ein gültiges und vertrauenswürdiges Zertifikat verwenden.