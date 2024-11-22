---
title: Konvertieren Sie HTML in PNG mit Aspose.HTML in .NET
linktitle: Konvertieren Sie HTML in PNG mit Aspose.HTML in .NET
second_title: Aspose.HTML .NET HTML-Manipulations-API
description: Erfahren Sie, wie Sie HTML-Dokumente mithilfe der Aspose.HTML-Bibliothek in .NET als PNG-Bilder konvertieren. Folgen Sie unserem Schritt-für-Schritt-Tutorial, um die Konvertierung von HTML in Bilder zu vereinfachen.
type: docs
weight: 10
url: /de/net/tutorials/html/converting-html-documents/convert-html-as-png/
---
## Einführung

Möchten Sie HTML-Dokumente mühelos in PNG-Bilder umwandeln? Dann sind Sie hier richtig! In diesem Tutorial erfahren Sie, wie Sie mit Aspose.HTML für .NET HTML als PNG-Bilder rendern. Diese leistungsstarke Bibliothek vereinfacht die Handhabung von HTML-Inhalten in .NET-Anwendungen und macht das Konvertieren von Webseiten oder Dokumentvorlagen in Bildformate zum Kinderspiel.

## Voraussetzungen

Bevor wir uns in den Code stürzen, stellen wir sicher, dass Sie alles richtig eingerichtet haben:

1.  .NET Framework/ .NET Core: Stellen Sie sicher, dass entweder das .NET Framework oder .NET Core auf Ihrem Computer installiert ist. Sie können herunterladen[.NET hier](https://dotnet.microsoft.com/download).

2.  Aspose.HTML für .NET-Bibliothek: Sie benötigen die Aspose.HTML-Bibliothek. Sie können sie herunterladen[Hier](https://releases.aspose.com/html/net/)oder testen Sie es kostenlos mit einem[Kostenlose Testversion](https://releases.aspose.com/).

3. IDE: Zum Schreiben und Ausführen Ihres Codes wird eine geeignete integrierte Entwicklungsumgebung (IDE) wie Visual Studio empfohlen.

4. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie den Anweisungen problemlos folgen. Aber keine Sorge, ich erkläre Ihnen alles im Laufe der Zeit!

Sobald diese Voraussetzungen erfüllt sind, können wir loslegen!

## Pakete importieren

Um die Aspose.HTML-Funktionen nutzen zu können, müssen wir die erforderlichen Namespaces importieren. So fügen Sie die Referenzen in Ihr Projekt ein:

1. Öffnen Sie Ihr Projekt in Visual Studio.
2. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt.
3. Wählen Sie „NuGet-Pakete verwalten“ aus.
4.  Suchen nach`Aspose.HTML` und installieren Sie es.

Sobald Sie das Paket installiert haben, können Sie mit dem Programmieren beginnen! Der erste Schritt besteht darin, Ihren Arbeitsbereich vorzubereiten und die relevanten Namespaces in Ihre C#-Datei aufzunehmen.

```csharp
using Aspose.Html;
using Aspose.Html.Converters;
using Aspose.Html.Rendering;
using Aspose.Html.Rendering.Image;
```

Nachdem wir nun die Szene gesetzt haben, wollen wir den Prozess des Renderns von HTML als PNG-Bild in detaillierte, leicht verständliche Schritte aufteilen.

## Schritt 1: Einrichten des Datenverzeichnisses

Als Erstes müssen Sie ein Verzeichnis einrichten, in dem Sie Ihre Bilder speichern. Dieses Verzeichnis dient als Ablage für die generierten PNG-Dateien.

```csharp
string dataDir = "Your Data Directory"; // Geben Sie Ihren Verzeichnispfad an
```

-  Ersetzen`"Your Data Directory"` mit dem Pfad, in dem Sie Ihre PNG-Ausgabedateien speichern möchten. Dies könnte etwa so aussehen:`@"C:\work\"`.

## Schritt 2: Erstellen Sie ein HTML-Dokumentobjekt

Nachdem wir nun unser Verzeichnis eingerichtet haben, erstellen wir ein HTML-Dokumentobjekt. Hier definieren wir den HTML-Inhalt, den wir konvertieren möchten.

```csharp
using (var document = new Aspose.Html.HTMLDocument("<style>p { color: green; }</style><p>my first paragraph</p>", dataDir))
{
    // Weitere Schritte finden Sie hier
}
```

-  Im obigen Code initialisieren wir ein neues`HTMLDocument` während Sie einige grundlegende HTML-Inhalte übergeben, die einen Absatz grün formatieren. Der zweite Parameter ist der Pfad, in dem alle Ressourcen (falls erforderlich) gespeichert werden.

## Schritt 3: Erstellen Sie einen HTML-Renderer

 Als nächstes erstellen wir eine Instanz des`HtmlRenderer` Klasse. Diese Klasse ist für die Darstellung unseres HTML-Dokuments im gewünschten Bildformat verantwortlich.

```csharp
using (HtmlRenderer renderer = new HtmlRenderer())
{
    // Weiter zum nächsten Schritt
}
```

-  Der`HtmlRenderer`ist Ihr bevorzugtes Objekt zum Umwandeln von HTML-Inhalten in Bilder. Es übernimmt den Rendering-Prozess im Hintergrund, sodass Sie sich auf das konzentrieren können, was Sie brauchen!

## Schritt 4: Einrichten des Bildgeräts

 Jetzt ist es Zeit, die`ImageDevice`Dies ist das Ziel für unseren Rendering-Prozess, in dem das endgültige PNG-Bild erstellt wird.

```csharp
using (ImageDevice device = new ImageDevice(dataDir + @"document_out.png"))
{
    // Rendern des HTML-Dokuments
}
```

- `ImageDevice` nimmt den vollständigen Pfad der zu erstellenden PNG-Datei an. Hier geben wir an, dass sie gespeichert werden soll als`document_out.png` in unserem zuvor definierten Verzeichnis.

## Schritt 5: Rendern Sie das HTML-Dokument in PNG

Jetzt kommt der spannende Teil – das Rendern unseres HTML-Dokuments in ein PNG-Bild! Hier rufen wir die Rendermethode auf, um die Konvertierung abzuschließen.

```csharp
renderer.Render(device, document);
```

-  Mit dem`Render` Methode der`HtmlRenderer` , Sie passieren die`ImageDevice` und die`HTMLDocument`. Diese Aktion konvertiert unser angegebenes HTML in ein PNG-Bild und das Bild wird in dem zuvor angegebenen Verzeichnis gespeichert.

## Abschluss

Und da haben Sie es! Sie haben HTML erfolgreich als PNG-Bild mit Aspose.HTML in .NET gerendert. Dieses leistungsstarke Tool bietet eine unkomplizierte Möglichkeit, HTML-Inhalte programmgesteuert zu bearbeiten, wodurch die Dokumenterstellung und -präsentation einfacher denn je wird. Egal, ob Sie an Webanwendungen arbeiten oder Berichte erstellen, diese Methode ist bahnbrechend.

## Häufig gestellte Fragen

### Was ist Aspose.HTML für .NET?
Aspose.HTML für .NET ist eine Bibliothek, die es Entwicklern ermöglicht, mit HTML-Dokumenten in .NET-Anwendungen zu arbeiten und Funktionen zum Rendern, Konvertieren und Bearbeiten bietet.

### Kann ich Aspose.HTML ohne Lizenz verwenden?
Ja, Aspose bietet eine kostenlose Testversion an, mit der Sie die Funktionen erkunden können, bevor Sie einen Kauf tätigen.

### Welche Dateitypen kann Aspose.HTML konvertieren?
Aspose.HTML konvertiert hauptsächlich HTML-Dokumente in verschiedene Formate, darunter PNG, JPEG, PDF und viele mehr.

### Wo erhalte ich Support für Aspose.HTML?
 Sie können Unterstützung über das Aspose-Forum erhalten[Hier](https://forum.aspose.com/c/html/29).

### Ist Aspose.HTML mit .NET Core kompatibel?
Ja, Aspose.HTML ist mit .NET Core kompatibel und kann problemlos in .NET Core-Anwendungen verwendet werden.