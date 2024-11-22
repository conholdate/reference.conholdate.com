---
title: Erstellen Sie primitive 3D-Modelle
linktitle: Erstellen Sie primitive 3D-Modelle
second_title: Aspose.3D .NET API
description: Erfahren Sie, wie Sie einfache 3D-Modelle, einschließlich Boxen und Zylinder, erstellen und anpassen und diese mühelos im FBX-Format speichern.
type: docs
weight: 10
url: /de/net/tutorials/3d/guide-to-3d-modeling/create-primitive-3d-modeling/
---
## Einführung

Willkommen in der immersiven Welt der 3D-Modellierung mit Aspose.3D für .NET! In diesem umfassenden Tutorial führen wir Sie Schritt für Schritt durch den Prozess der Erstellung primitiver 3D-Modelle. Egal, ob Sie ein erfahrener Entwickler oder ein lernbegieriger Anfänger sind, mit diesem Leitfaden können Sie visuell beeindruckende 3D-Elemente für Ihre Projekte erstellen.

## Voraussetzungen

Bevor Sie mit der 3D-Modellierung beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

-  Aspose.3D für .NET: Laden Sie die Aspose.3D für .NET-Bibliothek herunter und installieren Sie sie von der[Download-Seite](https://releases.aspose.com/3d/net/).
  
- .NET-Entwicklungsumgebung: Richten Sie eine mit Aspose.3D kompatible Umgebung ein, beispielsweise Visual Studio.

Nachdem alles vorbereitet ist, begeben wir uns auf unser 3D-Modellierungsabenteuer!

## Importieren erforderlicher Namespaces

Beginnen Sie mit dem Importieren der erforderlichen Namespaces, um auf die Aspose.3D-Funktionen zuzugreifen:

```csharp
using System;
using System.IO;
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Formats;
```

Diese Namespaces bieten Ihnen die notwendigen Tools zum Bearbeiten von 3D-Modellen und Speichern Ihrer Kreationen.

## Schritt 1: Initialisieren Sie ein Szenenobjekt

Erstellen Sie ein neues Szenenobjekt, das als Leinwand für Ihre 3D-Modelle dient:

```csharp
// Initialisieren eines Szenenobjekts
Scene scene = new Scene();
```

Diese Szene enthält die Grundformen, die Sie erstellen möchten.

## Schritt 2: Erstellen Sie ein Boxmodell

Als Nächstes fügen wir Ihrer Szene ein Boxmodell hinzu:

```csharp
// Erstellen eines Boxmodells
scene.RootNode.CreateChildNode("box", new Box());
```

Sie können die Abmessungen und Eigenschaften der Box individuell an Ihre kreative Vision anpassen.

## Schritt 3: Erstellen Sie ein Zylindermodell

Verbessern Sie jetzt Ihre Szene, indem Sie einen Zylinder hinzufügen:

```csharp
// Erstellen eines Zylindermodells
scene.RootNode.CreateChildNode("cylinder", new Cylinder());
```

Genau wie bei der Box können Sie die Parameter des Zylinders anpassen, um das gewünschte Aussehen zu erzielen.

## Schritt 4: Speichern Sie die Szene im FBX-Format

Um Ihr 3D-Modell zu erhalten, speichern Sie es im FBX-Format:

```csharp
// Zeichnung im FBX-Format speichern
var output = Path.Combine("Your Output Directory", "test.fbx");
scene.Save(output, FileFormat.FBX7500ASCII);
```

Achten Sie darauf, ein geeignetes Ausgabeverzeichnis und einen geeigneten Dateinamen für Ihr Modell auszuwählen.

## Schritt 5: Eine Erfolgsmeldung anzeigen

Feiern Sie abschließend Ihren Erfolg mit der Anzeige einer Nachricht:

```csharp
// Erfolgsmeldung anzeigen
Console.WriteLine($"\nBuilding a scene from primitive 3D models was successful.\nFile saved at {output}");
```

Ihre aus primitiven Modellen bestehende 3D-Szene ist jetzt vollständig und gespeichert!

## Abschluss

 Herzlichen Glückwunsch zur Erstellung atemberaubender 3D-Modelle mit Aspose.3D für .NET! Dieses Tutorial behandelte die Grundlagen der primitiven Modellierung, aber die Möglichkeiten sind endlos. Erfahren Sie mehr über erweiterte Funktionen und Techniken im[Dokumentation](https://reference.aspose.com/3d/net/).

## Häufig gestellte Fragen

### Kann ich Aspose.3D für .NET mit anderen Programmiersprachen als .NET verwenden?

Aspose.3D unterstützt hauptsächlich .NET, es sind aber Versionen für Java und andere Plattformen verfügbar.

### Ist eine kostenlose Testversion verfügbar?

 Ja, Sie können die Funktionen von Aspose.3D ausprobieren mit einem[Kostenlose Testversion](https://releases.aspose.com/).

### Wo finde ich Unterstützung für Aspose.3D für .NET?

 Für Community-Support besuchen Sie die[Aspose.3D Forum](https://forum.aspose.com/c/3d/18).

### Wie kann ich eine vorläufige Lizenz erhalten?

 Sie können eine temporäre Lizenz anfordern[Hier](https://purchase.conholdate.com/temporary-license/).

### Gibt es zusätzliche Tutorials?

 Ja! Weitere Tutorials und Beispiele finden Sie im[Dokumentation](https://reference.aspose.com/3d/net/).