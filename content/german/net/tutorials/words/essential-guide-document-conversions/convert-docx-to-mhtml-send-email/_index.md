---
title: Konvertieren Sie DOCX in MHTML und senden Sie E-Mails mit Aspose.Words für .NET
linktitle: Konvertieren Sie DOCX in MHTML und senden Sie E-Mails mit Aspose.Words für .NET
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Dieser umfassende Leitfaden bietet eine Schritt-für-Schritt-Anleitung zum Konvertieren von DOCX-Dokumenten in das MHTML-Format und zum Versenden per E-Mail mithilfe der Bibliotheken Aspose.Words und Aspose.Email in .NET.
type: docs
weight: 10
url: /de/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Einführung

In der heutigen digitalen Landschaft ist das Konvertieren von Dokumenten zwischen Formaten und deren Versand per E-Mail eine gängige Aufgabe. Diese Anleitung führt Sie durch die Konvertierung einer DOCX-Datei in das MHTML-Format und den Versand per E-Mail mithilfe der leistungsstarken Aspose.Words- und Aspose.Email-Bibliotheken für .NET. Wir erläutern jeden Schritt klar und deutlich, damit Sie ihn problemlos nachvollziehen können. Lassen Sie uns beginnen!

## Voraussetzungen

Stellen Sie vor dem Eintauchen in den Prozess sicher, dass Sie Folgendes eingerichtet haben:

1.  Aspose.Words für .NET: Laden Sie die Bibliothek herunter und installieren Sie sie von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2.  Aspose.Email für .NET: Laden Sie diese Bibliothek herunter und installieren Sie sie von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/email/net/).
3. .NET Framework: Stellen Sie sicher, dass das .NET Framework auf Ihrem Computer installiert ist.
4. SMTP-Server: Sie benötigen Zugriff auf einen SMTP-Server, um E-Mails zu senden.

## Erforderliche Namespaces importieren

Um Aspose.Words und Aspose.Email in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie oben in Ihrer C#-Datei die folgenden using-Direktiven hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Schritt 1: Laden Sie das DOCX-Dokument

 Laden Sie zunächst das DOCX-Dokument, das Sie konvertieren möchten. Verwenden Sie die`Document` Klasse von Aspose.Words, um dies zu erreichen.

```csharp
// Geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Schritt 2: Speichern Sie das Dokument als MHTML

 Als nächstes konvertieren Sie das geladene Dokument in das MHTML-Format. Dies geschieht mit dem`Save` Methode der`Document` Klasse.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Setzt die Streamposition zum Lesen auf den Anfang zurück.
    stream.Position = 0;
}
```

## Schritt 3: Erstellen Sie eine E-Mail-Nachricht

Erstellen Sie nun eine E-Mail-Nachricht aus dem MHTML-Stream mit Aspose.Email. Sie verwenden die`MailMessage` Klasse für diesen Zweck.

```csharp
// Laden Sie den MHTML-Stream in eine Aspose.Email MIME-E-Mail-Nachricht.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Schritt 4: Senden Sie die E-Mail

 Zum Schluss senden Sie die E-Mail mit einem SMTP-Client. Konfigurieren Sie den SMTP-Client mit Ihren Serverdetails und verwenden Sie die`Send` Methode zum Versenden der Nachricht.

```csharp
// Konfigurieren und senden Sie die Nachricht mit Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Abschluss

Herzlichen Glückwunsch! Sie haben ein DOCX-Dokument erfolgreich in MHTML konvertiert und es mit Aspose.Words und Aspose.Email für .NET per E-Mail versendet. Dieser Vorgang umfasst das Laden des Dokuments, das Konvertieren in MHTML, das Erstellen einer E-Mail-Nachricht und das Senden über einen SMTP-Client. Mit diesen Schritten können Sie die Konvertierung und das Versenden von Dokumenten per E-Mail nahtlos in Ihren Anwendungen automatisieren.

## Häufig gestellte Fragen

### Kann ich mit dieser Methode andere Dokumentformate konvertieren?
Auf jeden Fall! Aspose.Words unterstützt eine Vielzahl von Formaten, sodass Sie DOC, DOCX, RTF und mehr in MHTML konvertieren können.

### Wie kann ich der E-Mail Anhänge hinzufügen?
 Sie können Anhänge ganz einfach hinzufügen mit dem`Attachments` Eigentum der`MailMessage` Klasse.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words ist mit .NET Core kompatibel und daher für die Verwendung in .NET Core-Anwendungen geeignet.

### Benötige ich eine Lizenz für Aspose.Words und Aspose.Email?
 Ja, beide Bibliotheken sind lizenzpflichtig. Eine temporäre Lizenz zu Testzwecken erhalten Sie bei[Aspose-Kaufseite](https://purchase.conholdate.com/temporary-license/).

### Wo finde ich weitere Dokumentation?
 Eine ausführliche Dokumentation finden Sie unter Aspose.Words[Hier](https://reference.aspose.com/words/net/) und Aspose.Email[Hier](https://reference.aspose.com/email/net/).