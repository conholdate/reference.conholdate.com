---
title: Hinzufügen benutzerdefinierter Dokumenteigenschaften in Word
linktitle: Hinzufügen benutzerdefinierter Dokumenteigenschaften in Word
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Ihre Word-Dokumente mit Aspose.Words für .NET mit benutzerdefinierten Dokumenteigenschaften verbessern. Diese umfassende Anleitung führt Sie durch den Prozess.
type: docs
weight: 10
url: /de/net/tutorials/words/mastering-document-properties/adding-custom-document-properties-in-word/
---
## Einführung

Willkommen! Wenn Sie Aspose.Words für .NET erkunden und erfahren möchten, wie Sie Ihren Word-Dateien benutzerdefinierte Dokumenteigenschaften hinzufügen, sind Sie hier richtig. Benutzerdefinierte Eigenschaften sind von unschätzbarem Wert für die Speicherung zusätzlicher Metadaten, die integrierte Eigenschaften nicht abdecken. Ob Sie Dokumentautorisierung, Revisionsnummern oder bestimmte Daten verfolgen müssen, benutzerdefinierte Eigenschaften können hilfreich sein. In diesem Tutorial führen wir Sie durch die Schritte zum nahtlosen Hinzufügen dieser Eigenschaften mit Aspose.Words für .NET. Lassen Sie uns anfangen!

## Voraussetzungen

Bevor Sie in den Code eintauchen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET-Bibliothek: Laden Sie es herunter[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio.
3. Grundkenntnisse in C#: Vertrautheit mit C# und .NET ist hilfreich.
4.  Beispieldokument: Bereiten Sie ein Beispiel-Word-Dokument mit dem Namen vor`Properties.docx` zur Änderung.

## Namespaces importieren

Um auf die Funktionen von Aspose.Words zuzugreifen, müssen Sie die erforderlichen Namespaces am Anfang Ihres Codes importieren:

```csharp
using System;
using Aspose.Words;
```

## Schritt 1: Einrichten des Dokumentpfads

 Als nächstes definieren wir den Pfad zu Ihrem Word-Dokument. Dieser Schritt ist wichtig, um Ihr`Properties.docx` Datei.

```csharp
// Geben Sie den Pfad zu Ihrem Dokumentverzeichnis an.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

 Ersetzen Sie unbedingt`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokument.

## Schritt 2: Zugriff auf benutzerdefinierte Dokumenteigenschaften

Greifen wir jetzt auf die benutzerdefinierten Dokumenteigenschaften des Word-Dokuments zu, in denen Ihre benutzerdefinierten Metadaten gespeichert werden.

```csharp
CustomDocumentProperties customDocumentProperties = doc.CustomDocumentProperties;
```

Über diese Zeile erhalten Sie Zugriff auf die Sammlung benutzerdefinierter Eigenschaften, mit denen Sie arbeiten werden.

## Schritt 3: Auf vorhandene Eigenschaften prüfen

Um Duplikate zu vermeiden, sollten Sie vor dem Hinzufügen neuer Eigenschaften prüfen, ob eine Eigenschaft bereits vorhanden ist.

```csharp
if (customDocumentProperties["Authorized"] != null) return;
```

Dieser Code prüft, ob die Eigenschaft „Authorized“ bereits vorhanden ist. Wenn dies der Fall ist, wird die Methode vorzeitig beendet, wodurch Duplikate vermieden werden.

## Schritt 4: Hinzufügen einer Booleschen Eigenschaft

Fügen wir eine benutzerdefinierte boolesche Eigenschaft hinzu, um anzugeben, ob das Dokument autorisiert ist.

```csharp
customDocumentProperties.Add("Authorized", true);
```

 Diese Zeile fügt eine Eigenschaft namens "Authorized" hinzu und setzt ihren Wert auf`true`.

## Schritt 5: Hinzufügen einer String-Eigenschaft

Als Nächstes geben wir durch Hinzufügen einer Zeichenfolgeneigenschaft an, wer das Dokument autorisiert hat.

```csharp
customDocumentProperties.Add("Authorized By", "John Smith");
```

Sie können „John Smith“ durch einen beliebigen Namen ersetzen.

## Schritt 6: Hinzufügen einer Datumseigenschaft

Um zu verfolgen, wann das Dokument autorisiert wurde, fügen wir eine Datumseigenschaft hinzu.

```csharp
customDocumentProperties.Add("Authorized Date", DateTime.Today);
```

 Diese Zeile fügt eine Eigenschaft namens "Autorisiertes Datum" hinzu und weist ihr das heutige Datum zu mit`DateTime.Today`.

## Schritt 7: Hinzufügen einer Revisionsnummer

Zur Versionskontrolle können wir eine Eigenschaft hinzufügen, um die Revisionsnummer des Dokuments zu verfolgen.

```csharp
customDocumentProperties.Add("Authorized Revision", doc.BuiltInDocumentProperties.RevisionNumber);
```

Hier fügen wir eine Eigenschaft „Autorisierte Revision“ hinzu, die die aktuelle Revisionsnummer des Dokuments enthält.

## Schritt 8: Hinzufügen einer numerischen Eigenschaft

Zum Schluss fügen wir eine numerische Eigenschaft hinzu, um einen autorisierten Betrag, beispielsweise einen Budgetbetrag, zu speichern.

```csharp
customDocumentProperties.Add("Authorized Amount", 123.45);
```

 Diese Zeile fügt eine Eigenschaft namens "Autorisierter Betrag" mit einem Wert von hinzu`123.45`. Sie können diese Zahl nach Bedarf anpassen.

## Abschluss

Herzlichen Glückwunsch! Sie haben erfolgreich benutzerdefinierte Dokumenteigenschaften zu einem Word-Dokument mit Aspose.Words für .NET hinzugefügt. Diese Eigenschaften sind eine leistungsstarke Möglichkeit, Metadaten zu speichern, die auf Ihre Anforderungen zugeschnitten sind, egal ob es sich um die Verfolgung von Autorisierungsdetails, Revisionsnummern oder bestimmten Beträgen handelt.

## Häufig gestellte Fragen

### Was sind benutzerdefinierte Dokumenteigenschaften?
Benutzerdefinierte Dokumenteigenschaften sind Metadaten, die Sie einem Word-Dokument hinzufügen können, um zusätzliche Informationen zu speichern, die nicht von integrierten Eigenschaften abgedeckt werden.

### Kann ich andere Eigenschaften als Zeichenfolgen und Zahlen hinzufügen?
Ja, Sie können verschiedene Arten von Eigenschaften hinzufügen, darunter Boolesche Werte, Daten und sogar benutzerdefinierte Objekte.

### Wie kann ich in einem Word-Dokument auf diese Eigenschaften zugreifen?
Sie können mit Aspose.Words programmgesteuert auf benutzerdefinierte Eigenschaften zugreifen oder diese direkt in Word über die Dokumenteigenschaften anzeigen.

### Ist es möglich, benutzerdefinierte Eigenschaften zu bearbeiten oder zu löschen?
Auf jeden Fall! Sie können benutzerdefinierte Eigenschaften mithilfe der von Aspose.Words bereitgestellten Methoden problemlos bearbeiten oder löschen.

### Können benutzerdefinierte Eigenschaften zum Filtern von Dokumenten verwendet werden?
Ja! Benutzerdefinierte Eigenschaften eignen sich hervorragend zum Kategorisieren und Filtern von Dokumenten basierend auf bestimmten Metadaten.