---
title: Rendern Sie Kalenderereignisse in MHTML mit Aspose.Email
linktitle: Rendern Sie Kalenderereignisse in MHTML mit Aspose.Email
second_title: Aspose.Email .NET E-Mail-Verarbeitungs-API
description: Rendern Sie Kalenderereignisse mit Aspose.Email für .NET in das MHTML-Format. Erfahren Sie Schritt für Schritt, wie Sie MSG-Dateien mit C# anpassen und speichern.
type: docs
weight: 15
url: /de/net/tutorials/email/handling-email-events-and-calendar/render-calendar-events-in-mhtml/
---
## Einführung

Aspose.Email für .NET ist eine leistungsstarke Bibliothek zur Handhabung von E-Mail-bezogenen Aufgaben in .NET-Anwendungen. Ein faszinierender Anwendungsfall ist das programmgesteuerte Rendern von Kalenderereignissen mit C#. Egal, ob Sie eine Kalenderintegrationsfunktion erstellen oder benutzerdefinierte E-Mail-Viewer erstellen, dieses Tutorial führt Sie durch das präzise und individuelle Rendern von Kalenderereignissen im MHTML-Format.

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass wir alles bereit haben, um diesem Tutorial folgen zu können:

1.  Aspose.Email für .NET-Bibliothek: Laden Sie die neueste Version der Bibliothek herunter von der[Aspose.Email für .NET-Downloadseite](https://releases.aspose.com/email/net/).
2. Entwicklungsumgebung: Visual Studio (oder Ihre bevorzugte C#-IDE) auf Ihrem System installiert.
3. Lizenz: Erwerben Sie eine gültige Lizenz für Aspose.Email. Zu Testzwecken können Sie eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/).
4.  Beispiel-MSG-Datei: Eine MSG-Datei für Kalenderereignisse. Sie können jede beliebige Datei verwenden.`.msg` Datei mit Kalenderereignissen, z. B. „Besprechung mit wiederkehrenden Vorkommnissen.msg“.

## Pakete importieren

Fügen Sie zunächst die erforderlichen Namespaces in Ihr Projekt ein. 

```csharp
using System;
using Aspose.Email;
using Aspose.Email.Mht;
```

Lassen Sie uns nun mit der Schritt-für-Schritt-Anleitung beginnen!

## Schritt 1: Laden Sie die MSG-Datei des Kalenderereignisses

Zuerst laden wir die MSG-Datei, die das Kalenderereignis enthält. Dieser Schritt ist wichtig, da er als Eingabe für die Darstellung des Ereignisses im MHTML-Format dient.


```csharp
string dataDir = "Your Data Directory";
string fileName = "Meeting with Recurring Occurrences.msg";

// Laden Sie die MSG-Datei
MailMessage msg = MailMessage.Load(dataDir + fileName);
```

- `dataDir`: Gibt das Verzeichnis an, in dem Ihre MSG-Datei gespeichert ist.
- `fileName`: Name der Kalenderereignisdatei.
- `MailMessage.Load` : Liest die Datei und lädt sie in ein`MailMessage` Objekt.

## Schritt 2: MHTML-Speicheroptionen konfigurieren

Als Nächstes konfigurieren wir die Optionen zum Rendern des Kalenderereignisses im MHTML-Format. Dazu gehört das Aktivieren bestimmter Formate, Überschriften und anderer Eigenschaften zur Anpassung.

```csharp
MhtSaveOptions options = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent
};
```

- `MhtSaveOptions`Stellt die Einstellungen zum Speichern von MHTML-Dateien dar.
- `MhtFormatOptions`: Konfiguriert Optionen wie das Einschließen von Kopfzeilen und das Rendern von Kalenderereignissen.

## Schritt 3: Anpassen der Anzeigevorlagen

Hier definieren wir, wie bestimmte Eigenschaften, wie beispielsweise die Startzeit des Ereignisses, in der Ausgabe erscheinen sollen. Dieser Schritt ermöglicht eine hochgradig anpassbare und lesbare Ausgabe.


```csharp
if (options.FormatTemplates.ContainsKey(MhtTemplateName.Start))
    options.FormatTemplates[MhtTemplateName.Start] = @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>";
else
    options.FormatTemplates.Add(MhtTemplateName.Start, @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>");
```

- `MhtTemplateName.Start`: Bezieht sich auf die „Start“-Eigenschaft des Kalenderereignisses.
- `options.FormatTemplates`: Passt die Anzeigevorlage für bestimmte Eigenschaften an.

## Schritt 4: Speichern Sie das Kalenderereignis als MHTML

Speichern Sie abschließend das Kalenderereignis mit den konfigurierten Optionen in einer MHTML-Datei.


```csharp
msg.Save(dataDir + "Meeting with Recurring Occurrences.mhtml", options);
```

- `msg.Save`: Speichert die Nachricht im angegebenen Format und am angegebenen Ort.
- `Meeting with Recurring Occurrences.mhtml`: Name der Ausgabedatei.

## Abschluss

Das Rendern von Kalenderereignissen mit Aspose.Email für .NET ist sowohl effizient als auch hochgradig anpassbar. Indem Sie die oben genannten Schritte befolgen, können Sie Kalenderereignisse nahtlos in eine MHTML-Datei mit maßgeschneiderter Formatierung konvertieren.

## Häufig gestellte Fragen

### Was ist MHTML?
MHTML ist ein Webarchiv-Dateiformat, das HTML und zugehörige Ressourcen wie Bilder enthält und sich daher für die Darstellung und Freigabe von Kalenderereignissen eignet.

### Kann ich wiederkehrende Ereignisse rendern?
Ja! Aspose.Email unterstützt die Darstellung wiederkehrender Ereignisse und stellt sicher, dass alle Details genau erfasst werden.

### Ist eine Lizenz erforderlich?
 Ja, eine gültige Lizenz ist erforderlich. Sie können eine[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) zur Auswertung.

### Kann ich der Ausgabe benutzerdefinierte Eigenschaften hinzufügen?
 Auf jeden Fall! Sie können Vorlagen für zusätzliche Eigenschaften anpassen, indem Sie`FormatTemplates` Sammlung.

### Wie behebe ich Probleme?
 Besuchen Sie die[Aspose.Email-Supportforum](https://forum.aspose.com/c/email/12/) für fachkundige Unterstützung.