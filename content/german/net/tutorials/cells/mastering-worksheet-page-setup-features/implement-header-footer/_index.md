---
title: Implementieren Sie Kopf- und Fußzeilen mit Aspose.Cells für .NET
linktitle: Implementieren Sie Kopf- und Fußzeilen mit Aspose.Cells für .NET
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Entdecken Sie, wie Sie Ihre Excel-Dokumente verbessern können, indem Sie Kopf- und Fußzeilen mit Aspose.Cells für .NET programmgesteuert anpassen. Diese umfassende Anleitung führt Sie durch jeden Schritt – vom Einrichten Ihrer Arbeitsmappe bis zum dynamischen Einfügen des Arbeitsblattnamens.
type: docs
weight: 22
url: /de/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Einführung

Kopf- und Fußzeilen sind wesentliche Elemente in Excel-Tabellen und liefern wichtige Kontextinformationen wie Dateinamen, Daten und Seitenzahlen. Egal, ob Sie Berichte automatisieren oder dynamische Dateien generieren, Aspose.Cells für .NET vereinfacht das programmgesteuerte Anpassen von Kopf- und Fußzeilen. Diese Anleitung bietet eine schrittweise Anleitung zum Verbessern Ihrer Excel-Dateien mit ausgefeilten und professionellen Kopf- und Fußzeilen.

## Voraussetzungen

Stellen Sie vor dem Eintauchen sicher, dass Sie Folgendes haben:

1.  Aspose.Cells für .NET: Laden Sie es herunter und installieren Sie es von[Hier](https://releases.aspose.com/cells/net/).
2. IDE-Setup: Verwenden Sie Visual Studio oder Ihre bevorzugte IDE mit dem .NET-Framework.
3.  Lizenz: Beginnen Sie mit einer kostenlosen Testversion, aber ziehen Sie in Erwägung, eine Voll- oder temporäre Lizenz für die volle Funktionalität zu erwerben. Sie können[eine temporäre Lizenz erhalten](https://purchase.aspose.com/temporary-license/).

## Importieren erforderlicher Pakete

Beginnen Sie mit dem Importieren der erforderlichen Namespaces in Ihr Projekt:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die zum Arbeiten mit Kopf- und Fußzeilen und anderen Excel-Funktionen in Aspose.Cells erforderlich sind.

## Schritt 1: Erstellen Sie eine Arbeitsmappe und greifen Sie auf die Seiteneinrichtung zu

Erstellen Sie zunächst eine neue Arbeitsmappe und rufen Sie die Seiteneinrichtung des Arbeitsblatts auf. Hier ändern Sie die Kopf- und Fußzeileneinstellungen.

```csharp
// Definieren Sie den Pfad zum Speichern Ihres Dokuments
string dataDir = "Your Document Directory";

// Instanziieren eines Workbook-Objekts
Workbook excel = new Workbook();
```

 Hier ein`Workbook` Objekt stellt Ihre Excel-Datei dar. Das`PageSetup` Mit der Eigenschaft des Arbeitsblatts können Sie Kopf- und Fußzeilen anpassen.

## Schritt 2: Zugriff auf die Eigenschaften von Arbeitsblatt und Seiteneinrichtung

 Jedes Arbeitsblatt in Aspose.Cells hat eine`PageSetup` Eigenschaft, die Layout-Funktionen, einschließlich Kopf- und Fußzeilen, steuert. Erhalten Sie die`PageSetup` Objekt für Ihr Arbeitsblatt:

```csharp
// Holen Sie sich den Verweis auf das PageSetup des ersten Arbeitsblatts
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Jetzt,`pageSetup` enthält die erforderlichen Einstellungen zum Anpassen von Kopf- und Fußzeilen.

## Schritt 3: Linken Bereich der Kopfzeile festlegen

Überschriften bestehen aus drei Abschnitten: links, Mitte und rechts. Beginnen wir damit, den linken Abschnitt so einzustellen, dass der Arbeitsblattname angezeigt wird.

```csharp
// Legen Sie den Arbeitsblattnamen im linken Abschnitt der Kopfzeile fest
pageSetup.SetHeader(0, "&A");
```

 Verwenden von`&A`zeigt den Arbeitsblattnamen dynamisch an, was insbesondere bei Arbeitsmappen mit mehreren Blättern nützlich ist.

## Schritt 4: Datum und Uhrzeit in der Mitte der Kopfzeile hinzufügen

Fügen Sie als Nächstes das aktuelle Datum und die Uhrzeit zum mittleren Abschnitt der Kopfzeile hinzu und wenden Sie zur Formatierung eine benutzerdefinierte Schriftart an.

```csharp
// Datum und Uhrzeit im mittleren Bereich der Kopfzeile in Fettschrift einstellen
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

In dieser Zeile:
- `&D` fügt das aktuelle Datum ein.
- `&T` fügt die aktuelle Uhrzeit ein.
- `"Times New Roman,Bold"` verwendet eine fette Schriftart Times New Roman.

## Schritt 5: Dateinamen im rechten Abschnitt der Kopfzeile anzeigen

Um die Kopfzeile zu vervollständigen, zeigen Sie auf der rechten Seite den Dateinamen mit einer angegebenen Schriftgröße an.

```csharp
// Dateinamen im rechten Abschnitt der Kopfzeile mit benutzerdefinierter Schriftgröße anzeigen
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Hier,`&F` stellt den Dateinamen dar und`&12` setzt die Schriftgröße auf 12.

## Schritt 6: Fügen Sie dem linken Fußzeilenabschnitt benutzerdefinierten Text hinzu

Lassen Sie uns nun den linken Fußzeilenabschnitt mit benutzerdefiniertem Text und einem bestimmten Schriftstil einrichten.

```csharp
// Fügen Sie im linken Abschnitt der Fußzeile benutzerdefinierten Text mit Schriftstil hinzu
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

In diesem Beispiel der Text`123` ist in der Schriftart „Courier New“ in Größe 14 gestaltet, während der Rest in der Standardschriftart der Fußzeile verbleibt.

## Schritt 7: Seitenzahl in der Mitte der Fußzeile einfügen

Durch die Angabe von Seitenzahlen in der Fußzeile können Leser mehrseitige Dokumente leichter verfolgen.

```csharp
// Seitenzahl in den mittleren Bereich der Fußzeile einfügen
pageSetup.SetFooter(1, "&P");
```

 Der`&P` Der Code fügt die aktuelle Seitenzahl zum mittleren Abschnitt der Fußzeile hinzu.

## Schritt 8: Gesamtseitenzahl im rechten Fußzeilenbereich anzeigen

Vervollständigen Sie die Fußzeile, indem Sie im rechten Abschnitt die Gesamtseitenzahl anzeigen.

```csharp
// Gesamtseitenzahl im rechten Abschnitt der Fußzeile anzeigen
pageSetup.SetFooter(2, "&N");
```

 Der`&N` Der Code gibt die Gesamtseitenzahl an und informiert den Leser über die Länge des Dokuments.

## Schritt 9: Speichern der Arbeitsmappe

Speichern Sie abschließend die Arbeitsmappe, um eine Excel-Datei mit den angepassten Kopf- und Fußzeilen zu erstellen.

```csharp
// Speichern der Arbeitsmappe
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Diese Zeile speichert die Datei mit Ihren Anpassungen.

## Abschluss

Durch das Anpassen von Kopf- und Fußzeilen in Excel-Arbeitsblättern wird die Professionalität Ihrer Dokumente verbessert. Mit Aspose.Cells für .NET können Sie diese Elemente problemlos steuern, von der Anzeige von Arbeitsblattnamen bis zum Einfügen von benutzerdefiniertem Text, Daten, Uhrzeiten und dynamischen Seitenzahlen. Nachdem Sie nun die Schritte gelernt haben, können Sie Ihre Excel-Automatisierungsprojekte verbessern.

## Häufig gestellte Fragen

### Kann ich für unterschiedliche Abschnitte von Kopf- und Fußzeilen unterschiedliche Schriftarten verwenden?
Ja, mit Aspose.Cells können Sie für jeden Abschnitt der Kopf- und Fußzeile eindeutige Schriftarten angeben.

### Wie entferne ich Kopf- und Fußzeilen?
 Löschen Sie Kopf- und Fußzeilen, indem Sie deren Text auf eine leere Zeichenfolge setzen mit`SetHeader` oder`SetFooter`.

### Kann ich mit Aspose.Cells für .NET Bilder in Kopf- oder Fußzeilen einfügen?
Derzeit unterstützt Aspose.Cells hauptsächlich Text in Kopf- und Fußzeilen. Für Bilder sind möglicherweise alternative Methoden erforderlich, z. B. das direkte Einfügen in das Arbeitsblatt.

### Unterstützt Aspose.Cells dynamische Daten in Kopf- und Fußzeilen?  
 Ja, Sie können verschiedene dynamische Codes verwenden (wie`&D`für Datum oder`&P` für die Seitenzahl), um dynamischen Inhalt hinzuzufügen.

### Wie kann ich die Höhe der Kopf- oder Fußzeile anpassen?  
 Aspose.Cells bietet Optionen innerhalb der`PageSetup` Klasse zum Anpassen der Kopf- und Fußzeilenränder, sodass Sie die Abstände steuern können.