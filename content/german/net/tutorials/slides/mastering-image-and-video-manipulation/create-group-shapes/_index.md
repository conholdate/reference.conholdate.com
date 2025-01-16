---
title: Erstellen Sie Gruppenformen in PowerPoint mit Aspose.Slides für .NET
linktitle: Erstellen Sie Gruppenformen in PowerPoint mit Aspose.Slides für .NET
second_title: Aspose.Slides .NET PowerPoint-Verarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Slides für .NET Gruppenformen erstellen und verwalten. Dieses umfassende Handbuch enthält klare, schrittweise Anweisungen.
type: docs
weight: 11
url: /de/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Einführung

Die Verbesserung der optischen Attraktivität und Organisation Ihrer PowerPoint-Präsentationen kann die Aufmerksamkeit Ihres Publikums erheblich steigern. Eine effektive Methode, dies zu erreichen, sind Gruppierungsformen. In diesem Tutorial erfahren Sie, wie Sie Aspose.Slides für .NET nutzen können, um Gruppierungsformen in Ihren Präsentationen zu erstellen und zu bearbeiten.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Slides für .NET: Laden Sie die neueste Version der Aspose.Slides-Bibliothek herunter und installieren Sie sie von der[Aspose-Website](https://releases.aspose.com/slides/net/).
- Entwicklungsumgebung: Richten Sie eine .NET-kompatible IDE wie Visual Studio ein, um an Ihrem Projekt zu arbeiten.
- Grundlegende C#-Kenntnisse: Machen Sie sich mit den grundlegenden C#-Konzepten vertraut.


## Erforderliche Namespaces importieren

Beginnen Sie in Ihrem C#-Projekt mit der Einbindung der folgenden Namespaces:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Schritt 1: Instanziieren der Präsentationsklasse

 Erstellen Sie eine Instanz des`Presentation`Klasse, in der Sie an Ihren Folien arbeiten werden. Geben Sie das Verzeichnis an, in dem Ihre Dokumente gespeichert sind:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // Schritte zum Erstellen und Bearbeiten von Formen finden Sie hier
}
```

## Schritt 2: Zugriff auf die erste Folie

Rufen Sie die erste Folie Ihrer neu erstellten Präsentation ab:

```csharp
ISlide slide = pres.Slides[0];
```

## Schritt 3: Zugriff auf die Shape-Sammlung

Holen Sie sich die Sammlung von Formen auf der Folie:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Schritt 4: Eine Gruppenform hinzufügen

Jetzt ist es an der Zeit, der Folie eine Gruppenform hinzuzufügen:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Schritt 5: Formen innerhalb der Gruppe hinzufügen

Sie können die Gruppenform mit einzelnen Formen, beispielsweise Rechtecken, füllen:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Form 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Form 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Form 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Form 4
```

## Schritt 6: Definieren Sie den Rahmen für die Gruppenform

Durch das Setzen eines Rahmens für die Gruppenform erhält diese eine definierte Begrenzung:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Schritt 7: Speichern Sie die Präsentation

Speichern Sie abschließend Ihre geänderte Präsentation im angegebenen Verzeichnis:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Slides für .NET erfolgreich Gruppenformen in Ihren PowerPoint-Präsentationen erstellt. Indem Sie die Formen auf diese Weise organisieren, können Sie das visuelle Layout und die Übersichtlichkeit Ihrer Inhalte erheblich verbessern und Ihren Präsentationen so mehr Wirkung verleihen.

## Häufig gestellte Fragen

### Ist Aspose.Slides mit der neuesten Version von .NET kompatibel?

 Ja, Aspose.Slides wird regelmäßig aktualisiert, um die Kompatibilität mit den neuesten .NET-Versionen sicherzustellen. Überprüfen Sie die[Dokumentation](https://reference.aspose.com/slides/net/) für die neuesten Kompatibilitätsdetails.

### Kann ich Aspose.Slides vor dem Kauf ausprobieren?

 Auf jeden Fall! Sie können eine kostenlose Testversion herunterladen[Hier](https://releases.aspose.com/).

### Wo finde ich Unterstützung für Aspose.Slides-bezogene Fragen?

 Besuchen Sie die Aspose.Slides[Forum](https://forum.aspose.com/c/slides/11) für Community-Unterstützung und Diskussionen.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Slides?

 Sie können eine temporäre Lizenz anfordern[Hier](https://purchase.aspose.com/temporary-license/).

### Wo kann ich eine Volllizenz für Aspose.Slides erwerben?

 Sie können eine Lizenz erwerben bei der[Kaufseite](https://purchase.aspose.com/buy).