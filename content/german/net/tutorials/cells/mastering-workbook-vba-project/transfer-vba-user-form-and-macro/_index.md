---
title: Übertragen Sie VBA-Benutzerformulare und Makros zwischen Excel-Arbeitsmappen
linktitle: Übertragen Sie VBA-Benutzerformulare und Makros zwischen Excel-Arbeitsmappen
second_title: Aspose.Cells .NET Excel-Verarbeitungs-API
description: Nutzen Sie die Leistungsfähigkeit der Excel-Automatisierung mit diesem umfassenden Leitfaden zum Übertragen von VBA-Benutzerformularen und Makros zwischen Arbeitsmappen mithilfe von Aspose.Cells für .NET. Perfekt für Anfänger und erfahrene Entwickler.
type: docs
weight: 11
url: /de/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Einführung

Willkommen zu Ihrem ultimativen Leitfaden zur Verbesserung Ihrer Excel-Erfahrung mit VBA-Makros und Benutzerformularen! In diesem Tutorial erfahren Sie, wie Sie mithilfe der leistungsstarken Aspose.Cells-Bibliothek für .NET einen VBA-Makro-UserForm-Designer von einer Arbeitsmappe in eine andere übertragen. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, dieser Schritt-für-Schritt-Leitfaden vermittelt Ihnen das Wissen, Excel-Dateien programmgesteuert zu verarbeiten. Bereit, loszulegen? Dann legen wir los!

## Voraussetzungen
Bevor wir mit der Codierung beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. C#-Entwicklungsumgebung: Eine Arbeitsumgebung für die C#-Entwicklung. Visual Studio wird dringend empfohlen.
2.  Aspose.Cells für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Cells-Bibliothek in Ihr Projekt integrieren. Sie können ganz einfach[Laden Sie es hier herunter](https://releases.aspose.com/cells/net/).
3. Grundkenntnisse zu VBA und Excel-Makros: Wenn Sie mit VBA und der Funktionsweise von Excel-Makros vertraut sind, wird Ihr Verständnis dieses Tutorials verbessert.
4. Eine Excel-Datei mit einem Benutzerformular: Erstellen oder erhalten Sie eine Excel-Arbeitsmappe mit einem Benutzerformular (vorzugsweise mit aktivierten Makros, wie`.xlsm` Dateien).

## Importieren erforderlicher Pakete
Um die von Aspose.Cells bereitgestellten Funktionen zu nutzen, fügen Sie oben in Ihrer C#-Datei die folgenden Namespaces ein:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Diese Namespaces geben Ihnen Zugriff auf die leistungsstarken Tools, die in der Aspose.Cells-Bibliothek eingebettet sind.

## Schritt 1: Definieren Sie Ihre Quell- und Ausgabeverzeichnisse
Legen Sie zunächst den Speicherort Ihrer Dateien fest:

```csharp
// Definieren Sie die Quell- und Ausgabeverzeichnisse
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Ersetzen Sie die Platzhalterpfade durch die tatsächlichen Verzeichnisse, in denen Ihre Dateien gespeichert sind.

## Schritt 2: Erstellen Sie eine leere Zielarbeitsmappe
Erstellen Sie als Nächstes eine neue Arbeitsmappe, in die Sie das Benutzerformular und die Makros kopieren:

```csharp
// Erstellen einer leeren Zielarbeitsmappe
Workbook target = new Workbook();
```

Dadurch wird eine leere Arbeitsmappe initialisiert, die Ihnen als Leinwand für die bevorstehende Datenübertragung dient.

## Schritt 3: Laden Sie Ihre Vorlagenarbeitsmappe
Laden Sie die Arbeitsmappe, die Ihr Benutzerformular und Ihre Makros enthält:

```csharp
// Laden Sie die Excel-Datei mit dem VBA-Macro Designer-Benutzerformular
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Anpassen`"sampleDesignerForm.xlsm"` zum Namen Ihrer tatsächlichen Datei.

## Schritt 4: Arbeitsblätter in die Zielarbeitsmappe kopieren
Kopieren wir nun die Arbeitsblätter aus der Vorlage in die Zielarbeitsmappe:

```csharp
// Alle Vorlagenarbeitsblätter in die Zielarbeitsmappe kopieren
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Fügen Sie eine Nachricht in Zelle A2 des Zielarbeitsblatts hinzu
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Dieser Code durchläuft jedes Arbeitsblatt in der Vorlage und kopiert es in die Zielarbeitsmappe. Dadurch wird sichergestellt, dass alle Ihre Daten nahtlos übertragen werden.

## Schritt 5: VBA-Makros aus der Vorlage kopieren
Als Nächstes kopieren wir die VBA-Makros, einschließlich der UserForm Designer-Module, in die neue Arbeitsmappe:

```csharp
// Kopieren des VBA-Macro Designer UserForm von der Vorlage zum Ziel
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Kopieren Sie den Modulcode von ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Code und Daten anderer Module kopieren
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Abrufen des Benutzerformular-Designerspeichers
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Fügen Sie den Designerspeicher zum Ziel-VBA-Projekt hinzu
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Dieser Code stellt sicher, dass nicht nur der Code, sondern auch das Design des Benutzerformulars kopiert wird, sodass die Funktionalität Ihrer Makros erhalten bleibt.

## Schritt 6: Speichern der Zielarbeitsmappe
Nachdem der Kopiervorgang abgeschlossen ist, speichern Sie Ihre neue Arbeitsmappe:

```csharp
// Speichern der Zielarbeitsmappe
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Ändern Sie den Ausgabedateinamen nach Bedarf. Dieser Schritt erstellt Ihre benutzerdefinierte Arbeitsmappe mit Makros und Benutzerformularen.

## Schritt 7: Erfolg bestätigen
Drucken Sie abschließend eine Erfolgsmeldung auf der Konsole aus:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Diese einfache Zeile versichert Ihnen, dass Ihr Prozess reibungslos verlief – eine wichtige Bestätigung Ihrer harten Arbeit!

## Abschluss
Herzlichen Glückwunsch! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Cells für .NET einen VBA-Makro-Benutzerformular-Designer von einer Arbeitsmappe in eine andere kopieren. Auch wenn es zunächst entmutigend erscheinen mag, werden Sie mit der Zeit die Manipulation von Arbeitsmappen beherrschen. Denken Sie daran, dass es beim Programmieren ums Experimentieren geht. Zögern Sie also nicht, verschiedene Funktionen in Ihren Excel-Dateien auszuprobieren. Wenn Sie Fragen haben oder Hilfe benötigen, sind die Aspose-Foren und -Dokumentationen hervorragende Ressourcen für Unterstützung.

## Häufig gestellte Fragen

### Welche Excel-Versionen unterstützt Aspose.Cells?
Aspose.Cells unterstützt verschiedene Excel-Formate, darunter XLSX, XLSM, CSV und mehr.

### Kann ich Aspose.Cells kostenlos nutzen?
 Ja! Sie können mit einer kostenlosen Testversion beginnen, um die Bibliothek zu testen:[Kostenlose Testversion](https://releases.aspose.com/).

### Benötige ich Visual Studio, um diesen Code auszuführen?
Obwohl Visual Studio aufgrund seiner benutzerfreundlichen Funktionen empfohlen wird, ist jede C#-IDE, die die .NET-Entwicklung unterstützt, ausreichend.

### Wo finde ich weitere Beispiele und Dokumentation?
 Entdecken Sie die[Aspose.Cells-Dokumentation](https://reference.aspose.com/cells/net/) für weitere Beispiele und ausführliche Erklärungen.

### Wie löse ich Probleme bei der Verwendung von Aspose.Cells?
 Besuchen Sie die[Aspose Support Forum](https://forum.aspose.com/c/cells/9) für Hilfe von der Community und dem Aspose-Supportpersonal.