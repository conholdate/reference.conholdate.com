---
title: Benutzerdefinierte Reihenfolge von Informationen in MHTML mit Aspose.Email
linktitle: Benutzerdefinierte Reihenfolge von Informationen in MHTML mit Aspose.Email
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Email für .NET eine benutzerdefinierte Informationsreihenfolge in MHTML definieren.
type: docs
weight: 14
url: /de/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## Einführung

Das Erstellen umfangreicher E-Mail-Formate kann die Kommunikation erheblich verbessern, insbesondere beim Exportieren von E-Mails in verschiedene Dateiformate wie MHTML. Aspose.Email für .NET bietet Entwicklern ein leistungsstarkes Toolkit zum Bearbeiten von E-Mails, einschließlich der Definition einer benutzerdefinierten Reihenfolge für die Anzeige von Informationen beim Exportieren in MHTML. In diesem Handbuch werden die dafür erforderlichen Schritte erläutert, sodass Sie diese leicht nachvollziehen können, egal ob Sie ein erfahrener Entwickler oder Anfänger sind. Also, legen wir gleich los!

## Voraussetzungen

Bevor Sie mit der Definition der benutzerdefinierten Reihenfolge der Informationen in MHTML beginnen, müssen Sie einige Voraussetzungen von Ihrer Liste abhaken:

1. .NET-Entwicklungsumgebung: Stellen Sie sicher, dass Sie eine .NET-Entwicklungsumgebung eingerichtet haben. Sie können Visual Studio, Visual Studio Code oder jede andere kompatible IDE verwenden.

2.  Aspose.Email-Bibliothek: Sie müssen die Aspose.Email für .NET-Bibliothek installiert haben. Sie können die neueste Version von der herunterladen[Aspose-Veröffentlichungsseite](https://releases.aspose.com/email/net/).

3. Grundlegende Kenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, verstehen Sie den Code besser.

4.  Beispiel-E-Mail-Datei: Sie benötigen ein Beispiel`.eml` Datei (zum Beispiel`Attachments.eml`) zu Testzwecken.

Sobald Sie diese Voraussetzungen erfüllen, können Sie dem Lernprogramm folgen!

## Pakete importieren

Um mit Ihrem Code zu beginnen, müssen Sie die erforderlichen Namespaces aus der Aspose.Email-Bibliothek importieren. Dies ist wichtig, um auf alle Klassen und Methoden zuzugreifen, die zum Bearbeiten von E-Mail-Dateien erforderlich sind.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

Fügen Sie diese am Anfang Ihrer C#-Datei ein. Jetzt können Sie mit dem Programmieren loslegen!

Nachdem Sie nun alles eingerichtet haben, unterteilen wir das Tutorial in überschaubare Schritte.

## Schritt 1: Legen Sie Ihr Datenverzeichnis fest

Als Erstes müssen Sie ein Verzeichnis einrichten, in dem Ihre E-Mail-Dateien gespeichert werden. Dies kann jeder beliebige Pfad auf Ihrem lokalen Computer sein.

```csharp
string dataDir = "Your Data Directory";
```

 Ersetzen`"Your Data Directory"` mit dem tatsächlichen Pfad, auf dem Ihr`.eml` Datei befindet. Wenn Ihre Datei beispielsweise in`C:\Emails`würden Sie schreiben:

```csharp
string dataDir = @"C:\Emails\";
```

## Schritt 2: Laden Sie die E-Mail-Nachricht

Als nächstes laden Sie die`.eml` Datei in eine`MailMessage` Objekt. Dadurch können Sie den Inhalt und die Metadaten der E-Mail bearbeiten.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

Stellen Sie sicher, dass der Dateiname mit dem Namen im angegebenen Verzeichnis übereinstimmt. Wenn Ihre Datei einen anderen Namen hat, aktualisieren Sie den Dateinamen entsprechend.

## Schritt 3: MHTML-Speicheroptionen einrichten

Nachdem Sie Ihre E-Mail geladen haben, können Sie festlegen, wie Sie sie als MHTML speichern möchten. Sie können mit den Standardoptionen beginnen.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

Diese Zeile initialisiert die MHTML-Speicheroptionen und bereitet die Bühne für die spätere Anpassung der Kopfzeilen vor.

## Schritt 4: MHTML in Standardreihenfolge speichern

Speichern wir die E-Mail als MHTML in der Standardreihenfolge. So haben Sie eine Vergleichsbasis nach der Anpassung.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

 Führen Sie diese Zeile aus und überprüfen Sie das angegebene Verzeichnis. Sie sollten nun eine neue MHTML-Datei mit dem Namen sehen`CustomOrderOfInformationInMHTML_1.mhtml`. Öffnen Sie es, um zu sehen, wie die Informationen standardmäßig angezeigt werden.

## Schritt 5: Kopfzeilenreihenfolge anpassen

Jetzt kommt der spaßige Teil! Sie können angeben, welche Header in die MHTML-Ausgabe aufgenommen werden sollen und in welcher Reihenfolge. Wir beginnen mit einigen allgemeinen Headern.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

Indem Sie diese Kopfzeilen hinzufügen, teilen Sie Aspose mit, wie die E-Mail angezeigt werden soll.

## Schritt 6: MHTML mit benutzerdefinierter Reihenfolge speichern

Nach dem Anpassen der Kopfzeilen müssen Sie die E-Mail erneut als MHTML speichern, um zu sehen, wie sich die neue Reihenfolge auf die Ausgabe auswirkt.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

 Führen Sie diesen Code aus und öffnen Sie`CustomOrderOfInformationInMHTML_2.mhtml`. Vergleichen Sie es mit dem ersten, um zu sehen, wie sich die Informationen aufgrund Ihrer Kopfzeilenreihenfolge geändert haben.

## Schritt 7: Kopfzeilenreihenfolge löschen und neu hinzufügen

Und wenn Sie eine ganz andere Reihenfolge wünschen? Sie können neu beginnen, indem Sie die vorhandenen Kopfzeileneinstellungen löschen.

```csharp
opt.RenderingHeaders.Clear();
```

Nun ist es an der Zeit, eine neue Reihenfolge für die Header festzulegen. Wenn Sie beispielsweise Anhänge priorisieren und Empfänger kopieren möchten:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## Schritt 8: MHTML mit neuer benutzerdefinierter Reihenfolge speichern

Abschließend speichern Sie die E-Mail ein letztes Mal mit den neuen Header-Einstellungen.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

 Nach dem Ausführen dieser Zeile öffnen Sie`CustomOrderOfInformationInMHTML_3.mhtml`und prüfen Sie, wie die Informationen basierend auf Ihrer neuen Anpassung präsentiert werden.

## Abschluss

Und da haben Sie es – eine unkomplizierte Anleitung zum Definieren einer benutzerdefinierten Reihenfolge von Informationen in MHTML mit Aspose.Email für .NET. Indem Sie diese Schritte befolgen, können Sie steuern, wie Ihre E-Mails im MHTML-Format dargestellt werden, und sicherstellen, dass die wichtigsten Informationen auf eine Weise präsentiert werden, die Ihren Anforderungen entspricht. 

## Häufig gestellte Fragen

### Was ist MHTML?
MHTML steht für „MIME HTML“, ein Archivformat für Webseiten, das HTML und andere Ressourcen wie Bilder kombiniert.

### Kann ich Aspose.Email kostenlos nutzen?
 Ja, Aspose bietet Entwicklern eine kostenlose Testversion an. Sie finden sie[Hier](https://releases.aspose.com/).

### Was ist, wenn bei der Verwendung von Aspose.Email Probleme auftreten?
 Unterstützung von der Community erhalten Sie über das[Aspose-Forum](https://forum.aspose.com/c/email/12/).

### Ist eine temporäre Lizenz für Aspose.Email verfügbar?
 Ja, Sie können eine vorläufige Lizenz beantragen[Hier](https://purchase.aspose.com/temporary-license/).

### Wo kann ich Aspose.Email kaufen?
 Sie können die Bibliothek hier erwerben[Link](https://purchase.aspose.com/buy).