---
title: Tworzenie kształtów grupowych w programie PowerPoint za pomocą Aspose.Slides dla platformy .NET
linktitle: Tworzenie kształtów grupowych w programie PowerPoint za pomocą Aspose.Slides dla platformy .NET
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Dowiedz się, jak tworzyć i zarządzać kształtami grupowymi za pomocą Aspose.Slides dla .NET. Ten kompleksowy przewodnik zawiera jasne instrukcje krok po kroku.
type: docs
weight: 11
url: /pl/net/tutorials/slides/mastering-image-and-video-manipulation/create-group-shapes/
---
## Wstęp

Poprawa atrakcyjności wizualnej i organizacji prezentacji PowerPoint może znacząco wpłynąć na zaangażowanie odbiorców. Jedną z efektywnych metod osiągnięcia tego jest grupowanie kształtów. W tym samouczku przyjrzymy się, jak wykorzystać Aspose.Slides dla .NET do tworzenia i manipulowania kształtami grup w prezentacjach.

## Wymagania wstępne

Zanim przejdziesz do samouczka, upewnij się, że posiadasz następujące rzeczy:

-  Aspose.Slides dla .NET: Pobierz i zainstaluj najnowszą wersję biblioteki Aspose.Slides ze strony[Strona internetowa Aspose](https://releases.aspose.com/slides/net/).
- Środowisko programistyczne: skonfiguruj środowisko IDE zgodne z platformą .NET, np. Visual Studio, aby pracować nad swoim projektem.
- Podstawowa wiedza o języku C#: Zapoznaj się z podstawowymi koncepcjami języka C#.


## Importuj niezbędne przestrzenie nazw

W swoim projekcie C# zacznij od uwzględnienia następujących przestrzeni nazw:

```csharp
using Aspose.Slides.Export;
using Aspose.Slides;
```

## Krok 1: Utwórz instancję klasy prezentacji

 Utwórz instancję`Presentation`klasa, w której będziesz pracować nad swoimi slajdami. Określ katalog, w którym przechowywane są Twoje dokumenty:

```csharp
string dataDir = "Your Documents Directory";
using (Presentation pres = new Presentation())
{
    // Tutaj znajdziesz kroki tworzenia i manipulowania kształtami
}
```

## Krok 2: Dostęp do pierwszego slajdu

Pobierz pierwszy slajd nowo utworzonej prezentacji:

```csharp
ISlide slide = pres.Slides[0];
```

## Krok 3: Uzyskaj dostęp do kolekcji kształtów

Pobierz kolekcję kształtów na slajdzie:

```csharp
IShapeCollection slideShapes = slide.Shapes;
```

## Krok 4: Dodaj kształt grupy

Teraz czas dodać kształt grupy do slajdu:

```csharp
IGroupShape groupShape = slideShapes.AddGroupShape();
```

## Krok 5: Dodaj kształty wewnątrz grupy

Możesz wypełnić grupę kształtów pojedynczymi kształtami, np. prostokątami:

```csharp
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 100, 100, 100); // Kształt 1
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 100, 100, 100); // Kształt 2
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 300, 300, 100, 100); // Kształt 3
groupShape.Shapes.AddAutoShape(ShapeType.Rectangle, 500, 300, 100, 100); // Kształt 4
```

## Krok 6: Zdefiniuj ramkę dla kształtu grupy

Ustawienie ramki dla kształtu grupy nadaje jej określoną granicę:

```csharp
groupShape.Frame = new ShapeFrame(100, 300, 500, 40, NullableBool.False, NullableBool.False, 0);
```

## Krok 7: Zapisz prezentację

Na koniec zapisz zmodyfikowaną prezentację w określonym katalogu:

```csharp
pres.Save(dataDir + "GroupShape_out.pptx", SaveFormat.Pptx);
```

## Wniosek

Gratulacje! Udało Ci się utworzyć kształty grupowe w prezentacjach PowerPoint przy użyciu Aspose.Slides dla .NET. Organizując kształty w ten sposób, możesz znacznie poprawić układ wizualny i przejrzystość treści, dzięki czemu Twoje prezentacje będą bardziej efektowne.

## Najczęściej zadawane pytania

### Czy Aspose.Slides jest kompatybilny z najnowszą wersją .NET?

 Tak, Aspose.Slides jest regularnie aktualizowany pod kątem zgodności z najnowszymi wersjami .NET. Sprawdź[dokumentacja](https://reference.aspose.com/slides/net/) Aby uzyskać najnowsze informacje na temat zgodności, zapoznaj się z treścią.

### Czy mogę wypróbować Aspose.Slides przed zakupem?

 Oczywiście! Możesz pobrać bezpłatną wersję próbną[Tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć pomoc dotyczącą zapytań związanych z Aspose.Slides?

 Odwiedź Aspose.Slides[forum](https://forum.aspose.com/c/slides/11) w celu uzyskania wsparcia społeczności i dyskusji.

### Jak uzyskać tymczasową licencję na Aspose.Slides?

 Możesz poprosić o tymczasową licencję[Tutaj](https://purchase.aspose.com/temporary-license/).

### Gdzie mogę nabyć pełną licencję na Aspose.Slides?

 Możesz kupić licencję od[strona zakupu](https://purchase.aspose.com/buy).