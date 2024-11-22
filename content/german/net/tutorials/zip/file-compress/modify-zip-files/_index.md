---
title: Zip-Dateien mit Aspose.Zip für .NET ändern
linktitle: Zip-Dateien ändern
second_title: Aspose.Zip .NET API zum Komprimieren und Archivieren von Dateien
description: Erfahren Sie, wie Sie ZIP-Dateien programmgesteuert effizient extrahieren, löschen und Einträge hinzufügen und so Ihre Möglichkeiten zur Dateibearbeitung verbessern.
type: docs
weight: 15
url: /de/net/tutorials/zip/file-compress/modify-zip-files/
---
## Einführung

ZIP-Dateien sind für die Datenorganisation und -komprimierung unerlässlich, aber wie ändern Sie deren Inhalt programmgesteuert? Die Lösung liegt in Aspose.Zip für .NET, einer robusten Bibliothek, die die Bearbeitung von ZIP-Dateien mit C# vereinfacht. In diesem Tutorial führen wir Sie Schritt für Schritt durch das Extrahieren, Löschen und Hinzufügen von Einträgen zu ZIP-Dateien.

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Zip für .NET-Bibliothek: Installieren Sie die Bibliothek in Ihrem Projekt. Sie können sie herunterladen[Hier](https://releases.aspose.com/zip/net/).
   
2. Dokumentverzeichnis: Richten Sie ein Verzeichnis zum Speichern Ihrer Zip-Dateien ein. Ersetzen Sie`"Your Document Directory"` im Code durch Ihren tatsächlichen Pfad.

## Erforderliche Namespaces importieren

Beginnen Sie mit dem Importieren der erforderlichen Namespaces:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Schritt 1: Öffnen Sie die äußere Zip-Datei

Beginnen Sie mit dem Öffnen Ihrer Hauptzip-Datei (äußere Zip-Datei):

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // Weiter mit der Identifizierung der inneren Zip-Einträge
}
```

## Schritt 2: Innere Zip-Einträge identifizieren

Identifizieren Sie als Nächstes alle inneren ZIP-Dateien und bereiten Sie deren Löschung vor:

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            // Innere Einträge extrahieren
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## Schritt 3: Innere Archiveinträge löschen

Wenn Sie die benötigten Einträge gesammelt haben, löschen Sie die inneren Zip-Einträge:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Schritt 4: Geänderte Einträge zum äußeren Zip hinzufügen

Jetzt können Sie die neu extrahierten Einträge wieder zu Ihrer äußeren ZIP-Datei hinzufügen:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Schritt 5: Speichern Sie die geänderte Zip-Datei

Speichern Sie abschließend Ihre Änderungen in einer neuen ZIP-Datei:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Abschluss

Aspose.Zip für .NET bietet eine leistungsstarke und unkomplizierte Möglichkeit, Zip-Dateien programmgesteuert zu bearbeiten. Dieses Tutorial behandelt das Extrahieren, Löschen und Hinzufügen von Einträgen zu einer Zip-Datei und veranschaulicht die Vielseitigkeit der Bibliothek. Erkunden Sie verschiedene Szenarien und verbessern Sie Ihre Fähigkeiten zur Dateibearbeitung!

## Häufig gestellte Fragen

### Kann ich Aspose.Zip für .NET mit anderen Programmiersprachen verwenden?
Aspose.Zip ist in erster Linie für .NET-Anwendungen konzipiert, aber Aspose bietet ähnliche Bibliotheken für verschiedene Programmiersprachen.

### Gibt es eine kostenlose Testversion für Aspose.Zip für .NET?
 Ja, eine kostenlose Testversion steht zum Download bereit[Hier](https://releases.aspose.com/).

### Wie erhalte ich Unterstützung für Aspose.Zip für .NET?
 Besuchen Sie die[Aspose.Zip-Forum](https://forum.aspose.com/c/zip/37) für Unterstützung und Diskussionen.

### Kann ich eine temporäre Lizenz für Aspose.Zip für .NET erwerben?
 Ja, Sie können eine vorübergehende Lizenz erhalten[Hier](https://purchase.conholdate.com/temporary-license/).

### Wo finde ich die Dokumentation für Aspose.Zip für .NET?
 Die komplette Dokumentation ist verfügbar[Hier](https://reference.aspose.com/zip/net/).