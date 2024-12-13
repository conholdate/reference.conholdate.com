---
title: Hinzufügen einer Ebene zu einer File-Geodatabase mit Aspose.GIS für .NET
linktitle: Hinzufügen eines Layers zu einer File-Geodatabase
second_title: Aspose.GIS .NET API
description: Erfahren Sie, wie Sie mit Aspose.GIS für .NET einer File Geodatabase (GDB) eine neue Ebene hinzufügen. Diese umfassende Anleitung behandelt Voraussetzungen, Namespace-Importe und detaillierte Schritte zum Erstellen und Validieren von Ebenen in Ihren GIS-Datensätzen.
type: docs
weight: 16
url: /de/net/tutorials/gis/mastering-layer-management/add-layer-to-file-geo-database/
---
## Einführung

Die Technologie des Geographischen Informationssystems (GIS) spielt eine zentrale Rolle bei der modernen Datenanalyse und -visualisierung. Aspose.GIS für .NET ist eine außergewöhnliche Bibliothek, die es Entwicklern ermöglicht, geografische Daten effizient zu bearbeiten. In dieser ausführlichen Anleitung erfahren Sie, wie Sie mit Aspose.GIS für .NET einem File Geodatabase (GDB)-Datensatz eine neue Ebene hinzufügen. Befolgen Sie diese umfassenden Schritte, um Ebenen nahtlos zu integrieren und Ihre GIS-Funktionen zu verbessern.

## Voraussetzungen für das Hinzufügen von Layern zu File-GDB

Bevor wir fortfahren, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.GIS für .NET-Bibliothek  
    Laden Sie die Bibliothek herunter und installieren Sie sie vom[Aspose.GIS für .NET-Seite](https://reference.aspose.com/gis/net/).

2. Ein File-Geodatabase-Dataset (GDB)  
   Stellen Sie sicher, dass Sie für den Vorgang über einen vorhandenen GDB-Datensatz verfügen.

3. Entwicklungsumgebung  
   Installieren und konfigurieren Sie Ihre bevorzugte IDE mit .NET-Unterstützung (z. B. Visual Studio).

4. Temporäre Lizenz (optional)  
    Für eine Evaluierung aller Funktionen fordern Sie bitte ein[vorläufige Lizenz](https://purchase.conholdate.com/temporary-license/).

5. Datenverzeichnis  
   Bereiten Sie ein Verzeichnis vor, um Ihre Eingabe- und Ausgabedatensätze zu verwalten.

## Importieren erforderlicher Namespaces

Schließen Sie vor dem Codieren die erforderlichen Namespaces ein, um auf die Aspose.GIS-Funktionen zuzugreifen. Fügen Sie am Anfang Ihres Projekts den folgenden Codeausschnitt hinzu:

```csharp
using Aspose.Gis;
using Aspose.Gis.Geometries;
using Aspose.Gis.SpatialReferencing;
using System;
```

## Schritt 1: Den GDB-Datensatz duplizieren

Um die Integrität Ihres ursprünglichen Datensatzes zu bewahren, erstellen Sie ein Duplikat. Verwenden Sie den folgenden Code, um den Datensatz an einen neuen Speicherort zu kopieren:

```csharp
string dataDir = "C:\\GISData\\"; // Verzeichnis mit Ihren Datensätzen
string originalPath = dataDir + "ExistingDataset.gdb";
string newDatasetPath = dataDir + "ModifiedDataset.gdb";

// Funktion zum Duplizieren des Verzeichnisses
RunExamples.CopyDirectory(originalPath, newDatasetPath);
```

## Schritt 2: Öffnen Sie den Datensatz und prüfen Sie die Erstellungsfunktion

Mit Aspose.GIS können Entwickler Datensätze öffnen und prüfen, ob neue Ebenen hinzugefügt werden können. Verwenden Sie den folgenden Codeausschnitt, um die Erstellungsfunktionen des Datensatzes zu bestätigen:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    Console.WriteLine($"Can Create Layers: {dataset.CanCreateLayers}"); // Sollte True zurückgeben.
}
```

## Schritt 3: Erstellen Sie eine neue Ebene im Datensatz

Zum Hinzufügen einer Ebene müssen das räumliche Bezugssystem und die Attribute definiert werden. So erstellen und füllen Sie eine Ebene mit Beispieldaten:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    // Erstellen Sie eine neue Ebene mit dem räumlichen Referenzsystem WGS 84
    using (var layer = dataset.CreateLayer("NewLayer", SpatialReferenceSystem.Wgs84))
    {
        // Hinzufügen eines Attributschemas
        layer.Attributes.Add(new FeatureAttribute("LocationName", AttributeDataType.String));

        // Erstellen und Hinzufügen einer Funktion
        var feature = layer.ConstructFeature();
        feature.SetValue("LocationName", "Sample Point");
        feature.Geometry = new Point(34.0522, -118.2437); // Längen- und Breitengrad
        layer.Add(feature);
    }
}
```

## Schritt 4: Öffnen und validieren Sie die neue Ebene

Nachdem Sie eine Ebene erstellt haben, validieren Sie deren Inhalt, um die Richtigkeit sicherzustellen. Verwenden Sie den folgenden Codeausschnitt:

```csharp
using (var dataset = Dataset.Open(newDatasetPath, Drivers.FileGdb))
{
    using (var layer = dataset.OpenLayer("NewLayer"))
    {
        Console.WriteLine($"Feature Count: {layer.Count}");
        Console.WriteLine($"Attribute Value: {layer[0].GetValue<string>("LocationName")}");
    }
}
```

## Abschluss

Das Hinzufügen einer Ebene zu einem File-Geodatabase-Datensatz mit Aspose.GIS für .NET ist ein unkomplizierter Vorgang, wenn Sie diese Schritte befolgen. Vom Duplizieren von Datensätzen bis zum Erstellen und Validieren von Ebenen bietet die Bibliothek robuste Tools zum Verwalten von GIS-Daten. Wenn Sie diese Techniken beherrschen, können Sie Ihre GIS-Workflows verbessern und eine effiziente geografische Datenmanipulation erreichen.

## Häufig gestellte Fragen

### Wofür wird Aspose.GIS für .NET verwendet?
Aspose.GIS für .NET ist eine Bibliothek zur Verarbeitung und Bearbeitung geografischer Daten und unterstützt verschiedene Dateiformate, darunter Shapefiles, GDB und mehr.

### Kann ich in einem einzigen Vorgang mehrere Ebenen hinzufügen?
Ja, Aspose.GIS ermöglicht das Erstellen und Verwalten mehrerer Ebenen innerhalb eines Datensatzes.

### Welche räumlichen Bezugssysteme werden unterstützt?
Die Bibliothek unterstützt zahlreiche räumliche Referenzsysteme, darunter WGS 84, NAD 83 und benutzerdefinierte CRS.

### Wo finde ich Unterstützung?
 Besuchen Sie die[Aspose.GIS-Forum](https://forum.aspose.com/c/gis/33) für Community-Diskussionen und -Unterstützung.

### Gibt es eine kostenlose Testversion?
 Ja, ein[Kostenlose Testversion](https://releases.aspose.com/) steht zum Testen der Funktionen der Bibliothek zur Verfügung.