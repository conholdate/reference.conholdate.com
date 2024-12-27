---
title: Erstellen Sie eine neue E-Mail-Nachricht in C# mit Aspose.Email für .NET
linktitle: Erstellen Sie eine neue E-Mail-Nachricht in C# mit Aspose.Email für .NET
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Email für .NET E-Mail-Funktionen nahtlos in Ihre C#-Anwendungen integrieren. Dieser umfassende Leitfaden bietet eine detaillierte Anleitung zum programmgesteuerten Erstellen, Formatieren und Senden von E-Mails.
type: docs
weight: 11
url: /de/net/tutorials/email/mastering-email-composition-and-creation/construct-a-new-mail-message-in-csharp/
---
## Einführung

Aspose.Email für .NET ist eine leistungsstarke Bibliothek, die Entwicklern dabei hilft, effizient mit E-Mails zu arbeiten. Sie unterstützt verschiedene Funktionen, darunter das Erstellen, Senden, Empfangen und Bearbeiten von E-Mails. In diesem Tutorial geht es um das Erstellen und Senden einer E-Mail-Nachricht von Grund auf.

## Einrichten Ihrer Entwicklungsumgebung

Stellen Sie vor dem Beginn sicher, dass Sie über eine C#-Entwicklungsumgebung verfügen. Sie können Visual Studio oder eine andere IDE Ihrer Wahl verwenden. 

### Installieren Sie Aspose.Email über NuGet

Um die Aspose.Email-Bibliothek zu Ihrem Projekt hinzuzufügen, führen Sie diese Schritte aus:

1. Öffnen Sie Ihr Projekt in Visual Studio.
2. Gehen Sie zu Tools > NuGet-Paket-Manager > NuGet-Pakete für Lösung verwalten.
3. Suchen Sie nach Aspose.Email und installieren Sie das Paket.

## Erstellen einer neuen E-Mail-Nachricht

 Nachdem Sie Aspose.Email installiert haben, erstellen wir eine neue E-Mail-Nachricht. Beginnen Sie mit der Erstellung einer Instanz des`MailMessage` Klasse, die eine E-Mail darstellt.

```csharp
using Aspose.Email;
using Aspose.Email.Smtp;

MailMessage message = new MailMessage();
```

## Angeben von E-Mail-Empfängern

 Geben Sie als nächstes die E-Mail-Empfänger an, indem Sie`To`, `Cc` , Und`Bcc` Eigenschaften der`MailMessage` Klasse.

```csharp
message.To.Add("recipient@example.com");
message.Cc.Add("cc@example.com");
message.Bcc.Add("bcc@example.com");
```

## Festlegen des Betreffs und des Texts der E-Mail

 Legen Sie den Betreff und den Text der E-Mail fest. Verwenden Sie dazu`Subject` Und`HtmlBody` Eigenschaften. Sie können bei Bedarf auch einfachen Text einfügen.

```csharp
message.Subject = "Hello from Aspose.Email!";
message.HtmlBody = "<p>This is the <b>HTML</b> body of the email.</p>";
```

## Anhänge hinzufügen

 Um Dateien an die E-Mail anzuhängen, verwenden Sie das`Attachments` Eigenschaft. So fügen Sie eine PDF-Datei hinzu:

```csharp
Attachment attachment = new Attachment("path/to/attachment.pdf");
message.Attachments.Add(attachment);
```

## Einbinden von Hyperlinks

 Sie können den E-Mail-Text verbessern, indem Sie mithilfe von HTML Hyperlinks hinzufügen`<a>` Stichworte.

```csharp
message.HtmlBody += "<p>Click <a href='https://example.com'>hier</a>, um unsere Website zu besuchen.</p>";
```

## Formatieren des E-Mail-Inhalts

Aspose.Email ermöglicht eine umfangreiche Formatierung mit HTML und CSS. Hier ist ein Beispiel für das Hinzufügen von formatiertem Text:

```csharp
message.HtmlBody += "<p style='color: blue;'>This text is blue.</p>";
```

## Senden der E-Mail

 Nachdem Sie die E-Mail-Nachricht erstellt haben, verwenden Sie die`SmtpClient` Klasse, um es zu senden. So geht's:

```csharp
SmtpClient client = new SmtpClient("smtp.example.com", 587, "your_username", "your_password");
try
{
    client.Send(message);
    Console.WriteLine("Email sent successfully.");
}
catch (Exception ex)
{
    Console.WriteLine("An error occurred: " + ex.Message);
}
```

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Email für .NET eine E-Mail erstellen und senden. Diese leistungsstarke Bibliothek vereinfacht die Integration von E-Mail-Funktionen in Ihre C#-Anwendungen und erleichtert die programmgesteuerte Kommunikation.

## Häufig gestellte Fragen

### Ist Aspose.Email eine kostenlose Bibliothek?
Aspose.Email bietet sowohl kostenlose als auch kostenpflichtige Versionen. Die kostenlose Version bietet eingeschränkte Funktionen, während die kostenpflichtige Version das volle Potenzial der Bibliothek freisetzt.

### Kann ich Anhänge beliebiger Größe senden?
Obwohl Aspose.Email keine strengen Beschränkungen auferlegt, müssen unbedingt die Beschränkungen des E-Mail-Anbieters hinsichtlich der Anhangsgröße und die Postfachkapazität des Empfängers berücksichtigt werden.

### Unterstützt Aspose.Email das Senden von E-Mails im Nur-Text-Format?
Ja, Sie können mit Aspose.Email problemlos sowohl HTML- als auch Nur-Text-E-Mails versenden.

### Ist es möglich, mit dieser Bibliothek E-Mails zu planen?
Aspose.Email konzentriert sich auf die Erstellung und Bearbeitung von E-Mails. Für die Planung von E-Mails müssen Sie ein separates Aufgabenplanungssystem integrieren.

### Wo finde ich weitere Beispiele und Dokumentation?
 Eine umfassende Dokumentation und Codebeispiele finden Sie auf der[Aspose.Email API-Referenz](https://reference.aspose.com/email/net/).