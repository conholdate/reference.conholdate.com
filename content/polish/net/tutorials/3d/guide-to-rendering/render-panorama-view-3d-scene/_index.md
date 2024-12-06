---
title: Renderowanie widoku panoramy sceny 3D przy użyciu Aspose.3D dla .NET
linktitle: Renderowanie widoku panoramicznego sceny 3D
second_title: Aspose.3D .NET API
description: Dowiedz się, jak renderować oszałamiający widok panoramiczny sceny 3D w aplikacjach .NET przy użyciu Aspose.3D. Postępuj zgodnie z naszym przewodnikiem krok po kroku dotyczącym renderowania scen immersyjnych.
type: docs
weight: 13
url: /pl/net/tutorials/3d/guide-to-rendering/render-panorama-view-3d-scene/
---
## Wstęp

Tworzenie wciągających, panoramicznych scen 3D to przełom dla deweloperów, którzy chcą ulepszyć swoje aplikacje za pomocą oszałamiających efektów wizualnych. Niezależnie od tego, czy pracujesz nad silnikiem gier, wizualizacją architektoniczną czy wciągającymi doświadczeniami internetowymi, renderowanie scen 3D jako panoram pozwala użytkownikom doświadczyć dynamicznego widoku ze wszystkich kątów. Aspose.3D dla .NET to idealne narzędzie do płynnej integracji tej funkcji z projektami .NET. Ten kompleksowy przewodnik przeprowadzi Cię przez proces renderowania panoramy ze sceny 3D za pomocą Aspose.3D dla .NET.

## Wymagania wstępne

Zanim rozpoczniesz proces renderowania, upewnij się, że masz następujące elementy:

- Aspose.3D dla .NET: Na początek musisz zainstalować Aspose.3D, który udostępnia wszystkie niezbędne narzędzia do obsługi zasobów 3D i renderowania.[Pobierz Aspose.3D dla .NET](https://releases.aspose.com/3d/net/) aby zacząć.
- Środowisko programistyczne .NET: Wymagane jest w pełni skonfigurowane środowisko programistyczne .NET. Upewnij się, że masz Visual Studio lub inne zgodne IDE.
-  Przykładowy plik sceny 3D: Możesz użyć dowolnej sceny 3D w formatach takich jak:`.glb`, `.fbx` , Lub`.obj`. W tym samouczku użyjemy prostego pliku „VirtualCity.glb”.

Gdy już spełnimy te wymagania wstępne, możemy przejść do przygotowania sceny.

## Importuj niezbędne przestrzenie nazw

Aby pracować z Aspose.3D, będziemy musieli zaimportować kilka przestrzeni nazw do naszego projektu. Te przestrzenie nazw umożliwiają wydajną manipulację obiektami 3D, ustawieniami kamery i opcjami renderowania.

```csharp
using Aspose.ThreeD;
using Aspose.ThreeD.Entities;
using Aspose.ThreeD.Render;
using Aspose.ThreeD.Utilities;
using System;
using System.Drawing;
using System.Drawing.Imaging;
```

Te przestrzenie nazw są niezbędne do załadowania sceny 3D, skonfigurowania kamery, oświetlenia i ustawienia tekstur renderowania, które tworzą widok panoramiczny.

## Krok 1: Załaduj scenę 3D do swojej aplikacji

 Pierwszym krokiem jest załadowanie sceny 3D do aplikacji. Można to osiągnąć za pomocą`Scene` klasa dostarczona przez Aspose.3D. Zastąp`"VirtualCity.glb"` ze ścieżką do pliku sceny 3D.

```csharp
Scene scene = new Scene("path_to_your_scene/VirtualCity.glb");
```

 Ten`Scene` Obiekt ładuje scenę 3D do pamięci, co pozwala na interakcję z nią i zastosowanie technik renderowania.

## Krok 2: Przygotuj kamerę i oświetlenie

Aby mieć pewność, że scena 3D zostanie uchwycona poprawnie, musisz ustawić kamerę i odpowiednie oświetlenie. Kamera pozwala kontrolować perspektywę sceny, a światła pomagają oświetlić obiekty.

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

- Konfiguracja kamery: Bliskie i dalekie płaszczyzny kamery są ustawione tak, aby określić widoczny zakres w scenie 3D.
- Konfiguracja oświetlenia: Dodano dwa światła — jedno punktowe i drugie o określonym kolorze, aby dodać scenie głębi i realizmu.

## Krok 3: Skonfiguruj renderer i zdefiniuj cele renderowania

Teraz, gdy scena, kamera i światła są ustawione, następnym krokiem jest utworzenie renderera i zdefiniowanie celów renderowania. Renderer odpowiada za generowanie obrazów 3D, a cele renderowania określają, gdzie zostanie zapisany ostateczny wynik.

```csharp
using (var renderer = Renderer.CreateRenderer())
{
    IRenderTexture rt = renderer.RenderFactory.CreateCubeRenderTexture(new RenderParameters(false), 512, 512);
    IRenderTexture final = renderer.RenderFactory.CreateRenderTexture(new RenderParameters(false, 32, 0, 0), 1024 * 3, 1024);
}
```

- Tekstura renderowania sześcianu: Służy do renderowania mapy sześcianu dla widoku panoramicznego. Definiujemy tutaj teksturę 512x512.
- Tekstura ostatecznego renderu: Jest to tekstura, która będzie zawierać ostateczny widok panoramiczny równokątny.

## Krok 4: Skonfiguruj obszar widoku i renderuj scenę

Po utworzeniu tekstur renderowania musimy skonfigurować obszar widoku, który definiuje obszar sceny 3D, który zostanie uchwycony przez kamerę.

```csharp
rt.CreateViewport(cam, RelativeRectangle.FromScale(0, 0, 1, 1));
renderer.Render(rt);
```

 Ten kod ustawia obszar widoku dla mapy sześciennej i renderuje scenę do`rt` renderuj teksturę.

## Krok 5: Zastosuj postprocessing do projekcji ekwirektangularnej

tym momencie musimy zastosować post-processing, aby przekształcić mapę sześcienną w panoramiczny widok równokątny. Ta transformacja zapewnia, że końcowy obraz będzie właściwą panoramą.

```csharp
PostProcessing equirectangular = renderer.GetPostProcessing("equirectangular");
equirectangular.Input = rt.Targets[0];
renderer.Execute(equirectangular, final);
```

- Projekcja równoodległościowa: Ten efekt przetwarzania końcowego przekształca mapę sześcienną w projekcję panoramiczną równoodległościową, zapewniając ciągły widok 360 stopni.

## Krok 6: Zapisz wyrenderowaną panoramę

Po zakończeniu renderowania i przetwarzania końcowego ostatnim krokiem jest zapisanie ostatecznej panoramy do pliku graficznego, np. PNG.

```csharp
((ITexture2D)final.Targets[0]).Save("Your_Output_Directory/panorama.png", ImageFormat.Png);
```

Obraz panoramiczny zostanie zapisany w określonym katalogu, co umożliwi zintegrowanie go z aplikacją lub wyświetlenie na stronie internetowej.

## Wniosek

Renderowanie panoramicznych widoków scen 3D nigdy nie było łatwiejsze dzięki Aspose.3D dla .NET. Postępując zgodnie z powyższymi krokami, możesz łatwo załadować scenę 3D, skonfigurować kamerę i światła, renderować scenę i stosować efekty post-processingu, aby generować immersyjne obrazy panoramiczne. Aspose.3D dla .NET zapewnia moc i elastyczność, aby ożywić wizualizacje 3D i bezproblemowo zintegrować je z aplikacjami.

## Najczęściej zadawane pytania

### Czy mogę wykorzystać własną scenę 3D do renderowania panoram?
Oczywiście. Po prostu zamień ścieżkę pliku przykładowej sceny na lokalizację swojej niestandardowej sceny 3D.

### Czy są dostępne jakieś dodatkowe efekty postprodukcji?
Tak, Aspose.3D oferuje szereg efektów postprodukcyjnych, takich jak głębia ostrości, rozmycie i wiele innych, które można zastosować w celu ulepszenia renderowanych obrazów.

### Jak mogę zoptymalizować wydajność renderowania?
Wydajność renderowania można zoptymalizować, dostosowując parametry, takie jak rozmiar i rozdzielczość tekstury renderowania, a także modyfikując bliskie i dalekie płaszczyzny kamery.

### Czy mogę zintegrować to z aplikacją internetową?
Tak, Aspose.3D for .NET można zintegrować z aplikacjami internetowymi .NET w celu dynamicznego renderowania panoram 3D.

### Czy istnieje forum społecznościowe poświęcone wsparciu Aspose.3D?
 Tak, możesz odwiedzić[Forum Aspose.3D](https://forum.aspose.com/c/3d/18) w celu uzyskania wsparcia i udziału w dyskusjach społecznościowych.