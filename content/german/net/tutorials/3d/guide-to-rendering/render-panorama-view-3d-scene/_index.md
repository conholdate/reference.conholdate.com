---
title: Rendern Sie eine Panoramaansicht einer 3D-Szene mit Aspose.3D für .NET
linktitle: Rendern einer Panoramaansicht einer 3D-Szene
second_title: Aspose.3D .NET API
description: Erfahren Sie, wie Sie mit Aspose.3D eine atemberaubende Panoramaansicht einer 3D-Szene in Ihren .NET-Anwendungen rendern. Folgen Sie unserer Schritt-für-Schritt-Anleitung für immersives Szenen-Rendering.
type: docs
weight: 13
url: /de/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Einführung

Das Erstellen immersiver, panoramischer 3D-Szenen ist ein Wendepunkt für Entwickler, die ihre Anwendungen mit atemberaubenden visuellen Effekten aufwerten möchten. Egal, ob Sie an einer Gaming-Engine, einer Architekturvisualisierung oder immersiven Web-Erlebnissen arbeiten, das Rendern von 3D-Szenen als Panoramen ermöglicht Benutzern eine dynamische Ansicht aus allen Winkeln. Aspose.3D für .NET ist das perfekte Tool, um diese Funktion nahtlos in Ihre .NET-Projekte zu integrieren. Diese umfassende Anleitung führt Sie durch den Prozess des Renderns eines Panoramas aus einer 3D-Szene mit Aspose.3D für .NET.

## Voraussetzungen

Stellen Sie vor dem Eintauchen in den Rendering-Prozess sicher, dass Folgendes vorhanden ist:

-  Aspose.3D für .NET: Zunächst müssen Sie Aspose.3D installieren, das alle erforderlichen Tools für die Handhabung von 3D-Assets und das Rendering bereitstellt.[Laden Sie Aspose.3D für .NET herunter](https://releases.aspose.com/3d/net/) um loszulegen.
- .NET-Entwicklungsumgebung: Eine vollständig konfigurierte .NET-Entwicklungsumgebung ist erforderlich. Stellen Sie sicher, dass Sie Visual Studio oder eine andere kompatible IDE haben.
- Beispieldatei für 3D-Szene: Sie können jede 3D-Szene in Formaten wie`.glb`, `.fbx` , oder`.obj`. Für dieses Tutorial verwenden wir eine einfache „VirtualCity.glb“-Datei.

Sobald Sie diese Voraussetzungen erfüllt haben, können wir mit dem Einrichten der Szene fortfahren.

## Erforderliche Namespaces importieren

Um mit Aspose.3D arbeiten zu können, müssen wir mehrere Namespaces in unser Projekt importieren. Mit diesen Namespaces können Sie 3D-Objekte, Kameraeinstellungen und Rendering-Optionen effizient bearbeiten.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Diese Namespaces sind wichtig für das Laden der 3D-Szene, das Konfigurieren der Kamera, der Beleuchtung und das Einrichten der Rendertexturen, die die Panoramaansicht bilden.

## Schritt 1: Laden Sie die 3D-Szene in Ihre Anwendung

 Der erste Schritt besteht darin, die 3D-Szene in Ihre Anwendung zu laden. Dies kann mithilfe des`Scene` Klasse bereitgestellt von Aspose.3D. Ersetzen`"VirtualCity.glb"` durch den Pfad zu Ihrer 3D-Szenendatei.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 Der`Scene` Das Objekt lädt die 3D-Szene in den Speicher, sodass Sie mit ihr interagieren und Rendering-Techniken anwenden können.

## Schritt 2: Kamera und Licht einrichten

Um sicherzustellen, dass Ihre 3D-Szene richtig aufgenommen wird, müssen Sie eine Kamera und die entsprechende Beleuchtung einrichten. Mit der Kamera können Sie die Perspektive der Szene steuern, während die Lichter dabei helfen, die Objekte zu beleuchten.

```csharp
Camera cam = new Camera(ProjectionType.Perspective)
{
    NearPlane = 0.1,
    FarPlane = 200,
    RotationMode = RotationMode.FixedDirection
};

scene.RootNode.CreateChildNode(cam).Transform.Translation = new Vector3(5, 6, 0);

scene.RootNode.CreateChildNode(new Light() 
{ 
    LightType = LightType.Point 
}).Transform.Translation = new Vector3(-10, 7, -10);

scene.RootNode.CreateChildNode(new Light() 
{ 
    Color = new Vector3(Color.CadetBlue) 
}).Transform.Translation = new Vector3(49, 0, 49);
```

- Kamera-Setup: Die Nah- und Fernebenen der Kamera werden so eingestellt, dass sie den sichtbaren Bereich in der 3D-Szene definieren.
- Licht-Setup: Es werden zwei Lichter hinzugefügt – ein Punktlicht und ein weiteres mit einer bestimmten Farbe, um der Szene Tiefe und Realismus zu verleihen.

## Schritt 3: Einrichten des Renderers und Definieren von Renderzielen

Nachdem Sie nun Ihre Szene, Kamera und Lichter eingestellt haben, besteht der nächste Schritt darin, den Renderer zu erstellen und die Renderziele zu definieren. Der Renderer ist für die Generierung der 3D-Bilder verantwortlich und Renderziele definieren, wo die endgültige Ausgabe gespeichert wird.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Cube Render Texture: Dies wird verwendet, um eine Cube-Map für die Panoramaansicht zu rendern. Wir definieren hier eine 512x512 Textur.
- Endgültige Rendertextur: Dies ist die Textur, die die endgültige äquirektanguläre Panoramaansicht enthält.

## Schritt 4: Konfigurieren Sie das Ansichtsfenster und rendern Sie die Szene

Nachdem wir die Rendertexturen erstellt haben, müssen wir das Ansichtsfenster konfigurieren, das den Bereich der 3D-Szene definiert, den die Kamera erfassen wird.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Dieser Code setzt den Viewport für die Cube Map und rendert die Szene in die`rt` Textur rendern.

## Schritt 5: Nachbearbeitung für äquirektanguläre Projektion anwenden

An diesem Punkt müssen wir eine Nachbearbeitung durchführen, um die Würfelkarte in eine äquirektanguläre Panoramaansicht umzuwandeln. Diese Transformation stellt sicher, dass das endgültige Bild ein richtiges Panorama ist.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Äquirektanguläre Projektion: Dieser Nachbearbeitungseffekt nimmt die Würfelkarte und wandelt sie in eine äquirektanguläre Panoramaprojektion um, die eine nahtlose 360-Grad-Ansicht bietet.

## Schritt 6: Speichern Sie das gerenderte Panorama

Sobald das Rendern und die Nachbearbeitung abgeschlossen sind, besteht der letzte Schritt darin, das endgültige Panorama in einer Bilddatei, beispielsweise einem PNG, zu speichern.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Dadurch wird das Panoramabild im angegebenen Verzeichnis gespeichert und Sie können es in Ihre Anwendung integrieren oder auf einer Website anzeigen.

## Abschluss

Das Rendern von Panoramaansichten von 3D-Szenen war mit Aspose.3D für .NET noch nie so einfach. Indem Sie die oben beschriebenen Schritte befolgen, können Sie ganz einfach eine 3D-Szene laden, Kamera und Beleuchtung konfigurieren, die Szene rendern und Nachbearbeitungseffekte anwenden, um immersive Panoramabilder zu erzeugen. Aspose.3D für .NET bietet die Leistung und Flexibilität, um Ihre 3D-Visualisierungen zum Leben zu erwecken und sie nahtlos in Ihre Anwendungen zu integrieren.

## Häufig gestellte Fragen

### Kann ich zum Rendern von Panoramen meine eigene 3D-Szene verwenden?
Auf jeden Fall. Ersetzen Sie einfach den Dateipfad der Beispielszene durch den Speicherort Ihrer benutzerdefinierten 3D-Szene.

### Sind zusätzliche Nachbearbeitungseffekte verfügbar?
Ja, Aspose.3D bietet eine Reihe von Nachbearbeitungseffekten wie Tiefenschärfe, Bloom und mehr, die zur Verbesserung Ihrer gerenderten Bilder angewendet werden können.

### Wie kann ich die Rendering-Leistung optimieren?
Die Rendering-Leistung kann durch Anpassen von Parametern wie Größe und Auflösung der Rendertextur sowie Feinabstimmung der Nah- und Fernebenen der Kamera optimiert werden.

### Kann ich dies in eine Webanwendung integrieren?
Ja, Aspose.3D für .NET kann in Ihre .NET-Webanwendungen integriert werden, um 3D-Panoramen dynamisch zu rendern.

### Gibt es ein Community-Forum für Aspose.3D-Support?
 Ja, Sie können die[Aspose.3D Forum](https://forum.aspose.com/c/3d/18) für Support und Community-Diskussionen.