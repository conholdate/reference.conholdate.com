---
title: Ändern der MHT-Schriftartanpassung mit C#
linktitle: Ändern der MHT-Schriftartanpassung mit C#
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Erfahren Sie, wie Sie Schriftarten während der MHT-Konvertierung mit Aspose.Email für .NET ändern. Folgen Sie dieser Schritt-für-Schritt-Anleitung zur einfachen Anpassung.
type: docs
weight: 11
url: /de/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## Einführung

In der Welt der Webkommunikation sind MHT-Dateien (MHTML) eine praktische Möglichkeit, Webinhalte mit Bildern, Links und Stilen zu speichern und zu teilen. Aber was passiert, wenn Sie diese MHT-Dateien durch Ändern der Schriftarten aufpeppen müssen? Dank Aspose.Email für .NET wird diese Aufgabe zum Kinderspiel. In diesem Tutorial führen wir Sie Schritt für Schritt durch den Prozess des Änderns von Schriftarten während der MHT-Konvertierung. Egal, ob Sie eine Anwendung entwickeln, die die E-Mail-Formatierung übernimmt, oder einfach nur Dokumente für Ihr Unternehmen anpassen möchten, dieser Leitfaden vermittelt Ihnen das nötige Wissen.

## Voraussetzungen

Bevor Sie sich in den Code vertiefen, sollten Sie einige wichtige Dinge vorbereitet haben:

1. Visual Studio: Sie benötigen eine integrierte Entwicklungsumgebung (IDE), um an Ihrem C#-Projekt zu arbeiten.
2.  Aspose.Email für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Bibliothek installiert haben. Sie können sie von der[Link](https://releases.aspose.com/email/net/).
3. .NET Framework: Ihr Projekt sollte mit dem .NET Framework kompatibel sein; normalerweise funktionieren .NET Core oder spätere Versionen gut.

Hast du alles vorbereitet? Super! Lass uns anfangen.

## Pakete importieren

Stellen Sie zunächst sicher, dass Ihr Projekt für die Verwendung der erforderlichen Namespaces eingerichtet ist. Sie sollten Folgendes am Anfang Ihrer C#-Datei einfügen:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

Diese Pakete geben Ihnen Zugriff auf die Funktionen, die Sie zum Arbeiten mit MHT-Dateien und zum Ändern ihrer Inhalte benötigen.

Lassen Sie uns nun die Schritte zum Ändern von Schriftarten während der MHT-Konvertierung aufschlüsseln.

## Schritt 1: Laden Sie die MHT-Datei

 Als erstes müssen Sie Ihre MHT-Datei in ein`MailMessage` Objekt. Hier können Sie auf den Inhalt zugreifen und ihn bearbeiten.

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 Erläuterung: Hier`"input.mht"` ist der Pfad zu Ihrer MHT-Datei. Der`MhtmlLoadOptions()`ermöglicht Ihnen die Konfiguration des Ladens der Datei, zum Beispiel die unterschiedliche Behandlung von Anhängen oder verknüpften Ressourcen.

## Schritt 2: Durch alternative Ansichten iterieren

MHT-Dateien haben oft mehrere alternative Ansichten, insbesondere wenn sie HTML-Inhalte enthalten. Sie müssen diese Ansichten durchlaufen, um die Ansicht zu finden, die Sie ändern möchten.

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 Erklärung: Sie überprüfen jeweils`AlternateView` um zu sehen, ob es vom Typ HTML ist. Wenn ja, können Sie darauf zugreifen`LinkedResources`, wo normalerweise alle im HTML verknüpften Schriftarten gespeichert sind.

## Schritt 3: Schriftarten identifizieren und anpassen

Da Sie nun Zugriff auf die verknüpften Ressourcen haben, können Sie ermitteln, bei welchen Ressourcen es sich um Schriftarten handelt, und diese nach Bedarf anpassen.

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // Zur gewünschten Schriftart wechseln
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // Stellen Sie sicher, dass es richtig codiert ist
    }
}
```

 Erklärung: Diese Schleife prüft, ob der Inhaltstyp der verknüpften Ressource eine TrueType-Schriftart ist. Wenn dies zutrifft, können Sie den Namen der Schriftart nach Belieben ändern (wie in diesem Beispiel „Arial“). Die`TransferEncoding`sollte ebenfalls festgelegt werden, um sicherzustellen, dass die Schriftdaten beim Speichern des Dokuments richtig codiert werden.

## Schritt 4: Speichern Sie die aktualisierte MHT-Datei

Nachdem Sie die Schriftarten angepasst haben, ist es an der Zeit, Ihre geänderte MHT-Datei zu speichern. Sie sollten sicherstellen, dass Sie die richtigen Speicheroptionen verwenden, um die Integrität Ihrer Datei zu wahren.

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 Erklärung: In dieser Codezeile`"output.mht"` ist der Name der Datei, in der Sie den aktualisierten Inhalt speichern möchten. Mit`SaveOptions.DefaultMhtml` stellt sicher, dass die neue Datei das MHT-Format beibehält.

## Abschluss

Das Ändern von Schriftarten in MHT-Dateien kann das Erscheinungsbild Ihrer Dokumente erheblich verbessern. Durch die Nutzung von Aspose.Email für .NET können Sie MHT-Dateien problemlos laden, ihren Inhalt ändern und die Änderungen mit nur wenigen Codezeilen speichern. Unabhängig davon, ob Sie an einem persönlichen Projekt oder einer größeren Anwendung arbeiten, kann die Beherrschung dieser Fähigkeiten die Art und Weise verbessern, wie Sie Informationen präsentieren.

## Häufig gestellte Fragen

### Was ist das MHT-Format?
MHT ist ein Archivformat für Webseiten, das HTML-Dokumente, Bilder und andere Ressourcen in einer einzigen Datei speichert.

### Kann ich mit Aspose andere Aspekte von MHT-Dateien ändern?
Auf jeden Fall! Mit Aspose.Email können Sie nahezu jeden Aspekt von MHT-Dateien ändern, einschließlich Anhängen, Kopfzeilen und mehr.

### Ist Aspose.Email für .NET kostenlos?
 Aspose bietet eine kostenlose Testversion an, für die Vollversion ist jedoch eine Lizenz erforderlich. Sie können eine temporäre Lizenz erhalten von[Hier](https://purchase.aspose.com/temporary-license/).

### Wo finde ich weitere Dokumentation zu Aspose.Email?
 Ausführliche Dokumentationen und Beispiele finden Sie unter[Aspose Email-Dokumentationsseite](https://reference.aspose.com/email/net/).

### Was ist, wenn bei der Verwendung von Aspose Probleme auftreten?
 Wenn Sie auf Probleme stoßen, können Sie sich an den Support wenden unter[Aspose-Supportforum](https://forum.aspose.com/c/email/12/).