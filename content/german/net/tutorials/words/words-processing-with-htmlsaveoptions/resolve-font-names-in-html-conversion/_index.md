---
title: Auflösen von Schriftnamen bei der HTML-Konvertierung
linktitle: Auflösen von Schriftnamen bei der HTML-Konvertierung
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Schriftartprobleme beim Konvertieren von Word-Dokumenten in HTML mit Aspose.Words für .NET effektiv lösen. Diese Schritt-für-Schritt-Anleitung enthält klare Anweisungen zum Konfigurieren von Speicheroptionen, um sicherzustellen, dass Ihre Schriftarten im exportierten HTML-Format korrekt angezeigt werden.
type: docs
weight: 10
url: /de/net/tutorials/words/words-processing-with-htmlsaveoptions/resolve-font-names-in-html-conversion/
---
## Einführung

Hallo, Programmierkollege! Wenn Sie beim Speichern von Word-Dokumenten als HTML schon einmal Probleme mit Schriftarten hatten, sind Sie nicht allein. Schriftarten können knifflig sein, aber keine Sorge; diese Anleitung hilft Ihnen dabei, Schriftartnamen in Ihren Word-Dokumenten mithilfe von Aspose.Words für .NET aufzulösen. Lassen Sie uns Schritt für Schritt in den Prozess eintauchen, um sicherzustellen, dass Ihre Schriftarten im HTML-Format genau richtig aussehen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
2.  Eine gültige Lizenz: Erwerben Sie eine Lizenz[Hier](https://purchase.aspose.com/buy) oder holen Sie sich eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).
3. Grundkenntnisse in C# und .NET: Vertrautheit mit grundlegenden Programmierkonzepten in C# wird vorausgesetzt.
4. Visual Studio: Jede Version, die das .NET-Framework unterstützt, funktioniert.

Nachdem wir nun unsere Voraussetzungen geklärt haben, können wir loslegen!

## Erforderliche Namespaces importieren

Stellen Sie vor dem Codieren sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben. Dies ist für den Zugriff auf die Aspose.Words-Funktionen von entscheidender Bedeutung.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Einrichten des Dokumentverzeichnisses

Richten wir zunächst den Pfad zu Ihrem Dokumentverzeichnis ein. Dort befindet sich Ihr Word-Dokument und Sie speichern Ihre Ausgabe.

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

 Hier,`dataDir` enthält den Pfad zu Ihrem Dokumentverzeichnis. Ersetzen Sie`"YOUR_DOCUMENT_DIRECTORY"` durch den tatsächlichen Pfad auf Ihrem System.

## Schritt 2: Laden des Word-Dokuments

Als nächstes müssen wir das Word-Dokument laden, das wir verarbeiten möchten. Dieses Dokument sollte die Schriftarten enthalten, die Sie auflösen möchten.

```csharp
Document doc = new Document(dataDir + "MissingFont.docx");
```

 Wir schaffen eine`Document` Objekt und laden Sie das Word-Dokument mit dem Namen "MissingFont.docx" aus unserem`dataDir`.

## Schritt 3: Konfigurieren der HTML-Speicheroptionen

Richten wir nun die Optionen zum Speichern des Dokuments als HTML ein und stellen sicher, dass die Schriftnamen richtig aufgelöst werden.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    PrettyFormat = true,
    ResolveFontNames = true
};
```

 Wir erstellen eine Instanz von`HtmlSaveOptions` mit`SaveFormat.Html` . Der`PrettyFormat` Option macht die HTML-Ausgabe lesbarer und`ResolveFontNames` stellt sicher, dass Schriftnamen aufgelöst werden.

## Schritt 4: Speichern des Dokuments als HTML

Abschließend speichern wir das Dokument mit den konfigurierten Speicheroptionen als HTML-Datei.

```csharp
doc.Save(dataDir + "ResolvedFontNames.html", saveOptions);
```

 Wir nennen die`Save` Methode auf der`Document` Objekt, wobei der Ausgabepfad und die von uns konfigurierten Speicheroptionen angegeben werden. Dadurch wird eine HTML-Datei mit aufgelösten Schriftnamen generiert.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, haben Sie beim Konvertieren eines Word-Dokuments in HTML mit Aspose.Words für .NET erfolgreich Schriftnamen aufgelöst. Dies stellt nicht nur sicher, dass Ihre Schriftarten korrekt angezeigt werden, sondern sorgt auch dafür, dass Ihre HTML-Ausgabe elegant und professionell aussieht. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, ändern und konvertieren können.

### Wie installiere ich Aspose.Words für .NET?
 Sie können Aspose.Words für .NET herunterladen von[Hier](https://releases.aspose.com/words/net/). Befolgen Sie die Installationsanweisungen in der Dokumentation.

### Kann ich Aspose.Words für .NET ohne Lizenz verwenden?
 Ja, aber es wird einige Einschränkungen geben. Für die volle Funktionalität können Sie eine Lizenz erwerben[Hier](https://purchase.aspose.com/buy) oder holen Sie sich eine temporäre Lizenz[Hier](https://purchase.aspose.com/temporary-license/).

### Warum werden meine Schriftarten in HTML nicht richtig angezeigt?
 Dieses Problem kann auftreten, wenn die Schriftarten während der Konvertierung nicht richtig aufgelöst werden. Einstellung`ResolveFontNames = true` In`HtmlSaveOptions` kann helfen, dieses Problem zu beheben.

### Wo erhalte ich Support für Aspose.Words für .NET?
 Unterstützung erhalten Sie vom[Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).