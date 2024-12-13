---
title: Schützen von Zeilen im Arbeitsblatt mit Aspose.Cells
linktitle: Schützen von Zeilen im Arbeitsblatt mit Aspose.Cells
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Erfahren Sie, wie Sie vertrauliche Informationen in Ihren Excel-Arbeitsblättern sichern, indem Sie bestimmte Zeilen mit Aspose.Cells für .NET schützen. Dieses umfassende Tutorial deckt alles ab, vom Einrichten Ihrer Umgebung.
type: docs
weight: 18
url: /de/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Einführung

Das programmgesteuerte Arbeiten mit Excel-Dateien erfordert häufig nicht nur die Datenmanipulation, sondern auch den Datenschutz. Der Schutz bestimmter Zeilen in einem Arbeitsblatt kann entscheidend sein, um vertrauliche Informationen zu schützen oder versehentliche Änderungen zu verhindern. In diesem Tutorial erfahren Sie, wie Sie Zeilen in einem Excel-Arbeitsblatt mit Aspose.Cells für .NET schützen. Wir führen Sie durch die erforderlichen Schritte, vom Einrichten Ihrer Umgebung bis zur einfachen Implementierung von Zeilenschutzfunktionen.

## Voraussetzungen
Bevor Sie beginnen, stellen Sie sicher, dass Folgendes vorhanden ist:

1.  Aspose.Cells für .NET: Laden Sie es herunter und installieren Sie es von der[Aspose Cells-Downloadseite](https://releases.aspose.com/cells/net/).
2. Visual Studio oder eine beliebige .NET IDE: Sie benötigen eine Entwicklungsumgebung. Visual Studio wird empfohlen, aber jede .NET-kompatible IDE reicht aus.
3. Grundlegende C#-Kenntnisse: Wenn Sie mit der C#-Programmierung vertraut sind, können Sie den Beispielcode leichter nachvollziehen und ihn bei Bedarf ändern.
4.  Aspose.Cells API-Dokumentation: Lesen Sie die[Aspose.Cells für .NET-Dokumentation](https://reference.aspose.com/cells/net/) für einen Überblick über die Klassenstruktur und Methoden.

Wenn die Voraussetzungen gegeben sind, können wir mit der Umsetzung beginnen.

## Erforderliche Pakete importieren
Importieren Sie zunächst die erforderlichen Pakete in Ihr C#-Projekt. Diese Bibliotheken sind für die Interaktion mit Excel-Dateien unerlässlich.

```csharp
using System.IO;
using Aspose.Cells;
```

## Schritt 1: Erstellen Sie eine neue Arbeitsmappe und ein neues Arbeitsblatt
Bevor Sie Schutzeinstellungen anwenden, erstellen Sie eine neue Arbeitsmappe und wählen Sie das Arbeitsblatt aus, mit dem Sie arbeiten möchten.

```csharp
// Definieren Sie den Pfad zum Dokumentenverzeichnis.
string dataDir = "Your Document Directory";
// Erstellen Sie das Verzeichnis, falls es nicht existiert.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Erstellen Sie eine neue Arbeitsmappe und wählen Sie das erste Arbeitsblatt aus.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Schritt 2: Style- und StyleFlag-Objekte definieren
Definieren Sie die Stil- und Stilflaggenobjekte, mit denen Sie die Zelleneigenschaften ändern, beispielsweise sperren oder entsperren können.

```csharp
// Definieren Sie die Stil- und Stilflaggenobjekte.
Style style;
StyleFlag flag;
```

## Schritt 3: Alle Spalten im Arbeitsblatt entsperren
Standardmäßig sind alle Zellen in einem Excel-Arbeitsblatt gesperrt. Um nur bestimmte Zeilen zu schützen, entsperren Sie zuerst alle Spalten.

```csharp
// Durchlaufen Sie alle Spalten und entsperren Sie sie.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Schritt 4: Bestimmte Zeilen sperren
Sperren Sie nun die Zeilen, die Sie schützen möchten. In diesem Beispiel sperren wir die erste Zeile.

```csharp
// Sperren Sie die erste Reihe.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Sie können diesen Schritt für alle weiteren Zeilen wiederholen, die Sie sperren möchten.

## Schritt 5: Schützen Sie das Blatt
Wenn die erforderlichen Zeilen gesperrt sind, ist es an der Zeit, das Arbeitsblatt zu schützen. Dadurch werden Änderungen an den gesperrten Zeilen verhindert, sofern der Schutz nicht entfernt wird.

```csharp
// Schützen Sie das Blatt.
sheet.Protect(ProtectionType.All);
```

## Schritt 6: Speichern der Arbeitsmappe
Speichern Sie abschließend die Arbeitsmappe mit den vorgenommenen Änderungen. Sie können zwischen verschiedenen Formaten wählen, beispielsweise Excel 97-2003 oder neuere Versionen.

```csharp
// Speichern Sie die Excel-Datei.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Abschluss
Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie Zeilen in einem Excel-Arbeitsblatt mit Aspose.Cells für .NET schützen. Indem Sie diese Schritte befolgen, können Sie Zeilen oder Spalten nach Bedarf entsperren oder sperren und Schutz anwenden, um die Integrität Ihrer Daten zu wahren.

## Häufig gestellte Fragen
### Wie kann ich mehrere Zeilen gleichzeitig schützen?
Sie können mehrere Zeilenindizes durchlaufen und den Sperrstil auf jeden einzeln anwenden.

### Kann ich für den Blattschutz ein Passwort festlegen?
 Ja, Sie können ein Passwort an den`sheet.Protect()` Methode zum Erzwingen des Kennwortschutzes.

### Kann ich statt ganzer Spalten bestimmte Zellen entsperren?
Ja, Sie können einzelne Zellen entsperren, indem Sie ihre Stileigenschaften ändern, anstatt ganze Spalten zu entsperren.

### Was passiert, wenn ich versuche, eine geschützte Zeile zu bearbeiten?
Wenn eine Zeile geschützt ist, verhindert Excel jegliche Änderungen an den gesperrten Zellen, sofern das Blatt nicht ungeschützt ist.

### Kann ich bestimmte Bereiche innerhalb einer Zeile schützen?
 Ja! Sie können einzelne Bereiche in einer Reihe sperren, indem Sie die`IsLocked` Eigenschaft für bestimmte Zellen innerhalb dieses Bereichs.