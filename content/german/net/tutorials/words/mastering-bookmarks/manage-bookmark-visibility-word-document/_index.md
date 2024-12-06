---
title: Verwalten der Lesezeichensichtbarkeit in Word-Dokumenten
linktitle: Verwalten der Lesezeichensichtbarkeit in Word-Dokumenten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Entdecken Sie, wie Sie mit Aspose.Words für .NET die Sichtbarkeit von Inhalten in Word-Dokumenten fachmännisch steuern können. Diese Schritt-für-Schritt-Anleitung.
type: docs
weight: 10
url: /de/net/tutorials/words/mastering-bookmarks/manage-bookmark-visibility-word-document/
---
## Einführung

Sind Sie bereit, Ihre Fähigkeiten zur Dokumentbearbeitung mit Aspose.Words für .NET zu verbessern? Egal, ob Sie ein erfahrener Entwickler sind, der Dokumentaufgaben automatisiert, oder ein neugieriger Benutzer, der die programmgesteuerte Steuerung von Word-Dateien erkundet, dieser Leitfaden ist auf Sie zugeschnitten. Heute werden wir uns damit befassen, wie Sie Inhalte basierend auf Lesezeichen in einem Word-Dokument ein- und ausblenden können. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Visual Studio: Jede mit .NET kompatible Version.
2.  Aspose.Words für .NET: Laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
3. Grundlegende C#-Kenntnisse: Kenntnisse im Schreiben einfacher C#-Programme sind ausreichend.
4. Ein Beispiel für ein Word-Dokument: Bereiten Sie für dieses Tutorial ein Word-Dokument (z. B. „Bookmarks.docx“) mit Lesezeichen vor.

### Neues Projekt erstellen

1. Öffnen Sie Visual Studio und erstellen Sie ein neues Konsolen-App-Projekt (.NET Core). Nennen Sie es etwa „BookmarkVisibilityManager“.

### Installieren Sie Aspose.Words für .NET

Fügen Sie Aspose.Words über den NuGet-Paket-Manager zu Ihrem Projekt hinzu:

1. Navigieren Sie zu Tools > NuGet-Paket-Manager > NuGet-Pakete für Lösung verwalten.
2. Suchen Sie nach „Aspose.Words“.
3. Installieren Sie das Paket.

Nachdem Sie Ihr Projekt eingerichtet haben, können Sie mit dem Laden des Dokuments fortfahren.

## Namespaces importieren

Beginnen Sie mit dem Importieren der wesentlichen Namespaces. Diese stellen die Klassen und Methoden bereit, die zum Bearbeiten von Word-Dokumenten mit Aspose.Words erforderlich sind.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

## Schritt 1: Laden des Dokuments

Um das Word-Dokument bearbeiten zu können, müssen wir es zuerst laden. So geht's:

```csharp
// Definieren Sie den Pfad zu Ihrem Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Dieses Snippet setzt den Pfad zu Ihrem Dokumentverzeichnis und lädt das Dokument in ein`Document` Objekt.

## Schritt 2: Mit Lesezeichen versehenen Inhalt ein-/ausblenden

 Erstellen wir nun eine Methode, um die Sichtbarkeit von Inhalten basierend auf Lesezeichen umzuschalten. Wir nennen diese Methode`ShowHideBookmarkedContent`.

Hier ist die Methodenimplementierung:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    if (bm != null)
    {
        Node currentNode = bm.BookmarkStart;
        while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
        {
            if (currentNode.NodeType == NodeType.Run)
            {
                Run run = (Run)currentNode;
                run.Font.Hidden = isHidden;
            }
            currentNode = currentNode.NextSibling;
        }
    }
}
```

-  Lesezeichen abrufen:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` holt das angegebene Lesezeichen.
- Knotendurchlauf: Wir durchlaufen die Knoten innerhalb des Lesezeichens.
-  Sichtbarkeit umschalten: Für jeden`Run` Knoten (der einen Textabschnitt darstellt), setzen wir seinen`Hidden` Eigentum auf der Grundlage der`isHidden` Parameter.

## Schritt 3: Anwenden der Methode

Nachdem unsere Methode nun fertig ist, verwenden wir sie, um Inhalte innerhalb eines bestimmten Lesezeichens anzuzeigen oder auszublenden:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true); // Versteckt Inhalte in „MyBookmark1“
```

Diese Zeile verbirgt den mit dem Lesezeichen „MyBookmark1“ verknüpften Inhalt.

## Schritt 4: Speichern des Dokuments

Nachdem Sie Ihre Änderungen vorgenommen haben, vergessen Sie nicht, das geänderte Dokument zu speichern:

```csharp
doc.Save(dataDir + "UpdatedBookmarks.docx");
```

Dadurch wird das Dokument mit den aktualisierten Sichtbarkeitseinstellungen gespeichert.

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für .NET mit Lesezeichen versehene Inhalte in einem Word-Dokument ein- und ausblenden. Diese leistungsstarke Bibliothek vereinfacht die Dokumentbearbeitung und eignet sich ideal zum Automatisieren von Berichten, Erstellen von Vorlagen oder Experimentieren mit Word-Dateien. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich mehrere Lesezeichen gleichzeitig umschalten?
 Ja, rufen Sie einfach die`ShowHideBookmarkedContent` Methode für jedes Lesezeichen, das Sie umschalten möchten.

### Hat das Ausblenden von Inhalten Auswirkungen auf die Struktur des Dokuments?
Nein, das Ausblenden von Inhalten wirkt sich nur auf deren Sichtbarkeit aus. Der Inhalt bleibt im Dokument erhalten.

### Kann ich diese Methode für andere Arten von Inhalten verwenden?
Diese Methode ist speziell für Textläufe konzipiert. Für andere Inhaltstypen müssen Sie die Knotendurchlauflogik entsprechend anpassen.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words bietet eine kostenlose Testversion an[Hier](https://releases.aspose.com/) , aber für den produktiven Einsatz ist eine Volllizenz erforderlich. Sie können diese erwerben[Hier](https://purchase.aspose.com/buy).

### Wie erhalte ich Unterstützung, wenn Probleme auftreten?
 Für Support besuchen Sie das Aspose-Community-Forum[Hier](https://forum.aspose.com/c/words/8).