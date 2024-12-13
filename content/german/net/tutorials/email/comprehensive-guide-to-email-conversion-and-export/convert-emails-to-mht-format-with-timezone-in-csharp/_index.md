---
title: Konvertieren Sie E-Mails in C# in das MHT-Format mit Zeitzone
linktitle: Konvertieren Sie E-Mails in C# in das MHT-Format mit Zeitzone
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Diese ausführliche Anleitung enthält klare Anweisungen zum Konvertieren von E-Mail-Nachrichten in das MHT-Format und zum genauen Umgang mit Zeitzoneninformationen mithilfe der Aspose.Email-Bibliothek für .NET.
type: docs
weight: 12
url: /de/net/tutorials/email/comprehensive-guide-to-email-conversion-and-export/convert-emails-to-mht-format-with-timezone-in-csharp/
---
## Einführung

Das Konvertieren von E-Mail-Nachrichten in verschiedene Formate ist eine häufige Aufgabe in Softwareanwendungen, insbesondere in Szenarien, in denen Zeit- und Zeitzonendaten von entscheidender Bedeutung sind. Diese Anleitung führt Sie durch den Prozess der Konvertierung von E-Mails in das MHT-Format und stellt dabei sicher, dass die Zeitzoneninformationen genau erhalten bleiben.

## Einrichten Ihrer Entwicklungsumgebung

Stellen Sie zunächst sicher, dass Sie über eine geeignete Entwicklungsumgebung verfügen:

1. Installieren Sie Visual Studio: Stellen Sie sicher, dass auf Ihrem Computer eine kompatible Version von Visual Studio installiert ist.
2. Erstellen Sie ein neues C#-Projekt: Starten Sie Visual Studio und erstellen Sie ein neues C#-Projekt für Ihre E-Mail-Konvertierungsanwendung.

## Installieren von Aspose.Email für .NET

Aspose.Email für .NET ist eine leistungsstarke Bibliothek, die E-Mail-Verarbeitungsaufgaben vereinfacht. Befolgen Sie diese Schritte, um es zu installieren:

1. Öffnen Sie Ihr Projekt in Visual Studio.
2. Navigieren Sie zu Tools > NuGet-Paket-Manager > NuGet-Pakete für Lösung verwalten.
3. Suchen Sie nach Aspose.Email und installieren Sie das Paket.
```csharp
// Fügen Sie die erforderlichen Using-Anweisungen hinzu
using Aspose.Email;
```
## Laden und Analysieren von E-Mail-Nachrichten

Als Nächstes müssen Sie die E-Mail-Nachricht, die Sie konvertieren möchten, laden und analysieren. Verwenden Sie den folgenden Codeausschnitt:

```csharp
// Laden Sie die E-Mail-Nachricht
var message = MailMessage.Load("path/to/your/email.eml");

// Zugreifen auf Nachrichteneigenschaften
var subject = message.Subject;
var sender = message.From.Address;
// ... weitere Eigenschaften nach Bedarf
```

## Umgang mit Zeitzoneninformationen

Die genaue Verwaltung von Zeitzoneninformationen ist von entscheidender Bedeutung. Der folgende Codeausschnitt zeigt, wie Zeitzonendaten aus einer E-Mail-Nachricht extrahiert und verarbeitet werden:

```csharp
var timezone = message.TimezoneOffset;
var timezoneId = Timezone.GetIdFromOffset(timezone);
var timezoneInfo = TimeZoneInfo.FindSystemTimeZoneById(timezoneId);
// Sie können jetzt timezoneInfo verwenden, um Zeitzonenkonvertierungen durchzuführen
```

## Konvertieren von E-Mails in das MHT-Format

Führen wir nun die Kernkonvertierung in das MHT-Format mit Aspose.Email durch:

```csharp
// MHT-Speicheroptionen festlegen
var mhtOptions = MhtSaveOptions.DefaultMhtml;

// Erstellen Sie einen Speicherstream für die MHT-Ausgabe
using var mhtStream = new MemoryStream();
message.Save(mhtStream, mhtOptions);
```

## Speichern der MHT-Datei

Nachdem die E-Mail-Nachricht in das MHT-Format konvertiert wurde, ist es an der Zeit, sie als Datei zu speichern:

```csharp
// Speichern Sie den MHT-Stream in einer Datei
using var fileStream = new FileStream("output.mht", FileMode.Create);
mhtStream.Seek(0, SeekOrigin.Begin);
mhtStream.CopyTo(fileStream);
```

## Abschluss

In diesem Handbuch haben Sie gelernt, wie Sie E-Mail-Nachrichten in das MHT-Format konvertieren und dabei Zeitzoneninformationen mit Aspose.Email für .NET effektiv verarbeiten. Indem Sie diese Schritte befolgen und zusätzliche Anpassungsoptionen erkunden, können Sie die E-Mail-Konvertierungsfunktion nahtlos in Ihre Anwendungen integrieren.

## Häufig gestellte Fragen

### Wie gehe ich mit Anhängen während der E-Mail-Konvertierung um?

 Um Anhänge zu verwalten, verwenden Sie die`Attachments` Eigentum der`MailMessage` Klasse. Durchlaufen Sie die Anhänge und speichern Sie sie bei Bedarf während des Konvertierungsvorgangs.

### Kann ich mit Aspose.Email für .NET E-Mails in andere Formate konvertieren?

Absolut! Aspose.Email für .NET unterstützt verschiedene Formate, darunter MSG, EML, PST und mehr. Sie können die bereitgestellten Codebeispiele an Ihr gewünschtes Ausgabeformat anpassen.

### Bleiben die Zeitzoneninformationen im MHT-Format erhalten?

 Ja, die Zeitzoneninformationen bleiben während des Konvertierungsprozesses erhalten. Durch die Behandlung von Zeitzonenverschiebungen und die Verwendung der entsprechenden`TimeZoneInfo`Methoden können Sie eine genaue Zeitzonendarstellung in der MHT-Datei sicherstellen.

### Wo finde ich weitere Dokumentation und Updates zu Aspose.Email für .NET?

 Ausführliche Informationen und Aktualisierungen finden Sie in der Dokumentation:[Aspose.Email für .NET API-Referenz](https://reference.aspose.com/email/net/)

### Wie kann ich die neueste Version von Aspose.Email für .NET herunterladen?

 Sie können die neueste Version von der Release-Seite herunterladen:[Laden Sie Aspose.Email für .NET herunter](https://releases.aspose.com/email/net/)