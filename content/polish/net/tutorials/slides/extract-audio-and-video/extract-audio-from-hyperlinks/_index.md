---
title: Wyodrębnij dźwięk z hiperłączy w programie PowerPoint za pomocą Aspose.Slides
linktitle: Wyodrębnij dźwięk z hiperłączy
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Dowiedz się, jak wyodrębnić dźwięk z hiperłączy w prezentacjach PowerPoint za pomocą Aspose.Slides dla .NET. Ten przewodnik krok po kroku zawiera jasne instrukcje.
type: docs
weight: 12
url: /pl/net/tutorials/slides/extract-audio-and-video/extract-audio-from-hyperlinks/
---
## Wstęp

prezentacjach multimedialnych dźwięk znacząco zwiększa siłę oddziaływania slajdów. Jeśli kiedykolwiek natknąłeś się na prezentację PowerPoint z hiperłączami audio i zastanawiałeś się, jak wyodrębnić ten dźwięk do innych zastosowań, jesteś we właściwym miejscu. Ten przewodnik przeprowadzi Cię przez proces wyodrębniania dźwięku z hiperłączy w prezentacji PowerPoint przy użyciu biblioteki Aspose.Slides for .NET.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

### Biblioteka Aspose.Slides dla .NET

 Upewnij się, że masz zainstalowaną bibliotekę Aspose.Slides for .NET. Jeśli jeszcze tego nie zrobiłeś, możesz ją pobrać ze strony[Dokumentacja Aspose.Slides dla .NET](https://reference.aspose.com/slides/net/).

### Prezentacja PowerPoint z hiperłączami audio

Będziesz potrzebować prezentacji PowerPoint (PPTX) zawierającej hiperłącza z powiązanym dźwiękiem. Ta prezentacja będzie Twoim źródłem do ekstrakcji dźwięku.

## Importowanie wymaganych przestrzeni nazw

Aby efektywnie wykorzystać Aspose.Slides dla .NET, należy zaimportować następujące przestrzenie nazw do projektu C#:

```csharp
using System;
using System.IO;
using Aspose.Slides;
```

Teraz, gdy wszystko mamy już na swoim miejscu, możemy podzielić proces ekstrakcji na proste kroki.

## Krok 1: Zdefiniuj katalog dokumentów

 Zacznij od określenia katalogu, w którym znajduje się prezentacja PowerPoint. Zastąp`"Your Document Directory"` z rzeczywistą ścieżką.

```csharp
string dataDir = "Your Document Directory";
```

## Krok 2: Załaduj prezentację programu PowerPoint

 Następnie załaduj prezentację PowerPoint (PPTX) zawierającą hiperłącze audio. Zastąp`"HyperlinkSound.pptx"` z rzeczywistą nazwą pliku prezentacji.

```csharp
string pptxFile = Path.Combine(dataDir, "HyperlinkSound.pptx");

using (Presentation pres = new Presentation(pptxFile))
{
    // Przejdź do następnego kroku.
}
```

## Krok 3: Uzyskaj dostęp do dźwięku hiperłącza

Pobierz hiperłącze z pierwszego kształtu na pierwszym slajdzie. Jeśli to hiperłącze ma skojarzony dźwięk, możemy przystąpić do jego wyodrębnienia.

```csharp
IHyperlink link = pres.Slides[0].Shapes[0].HyperlinkClick;

if (link.Sound != null)
{
    // Przejdź do następnego kroku.
}
```

## Krok 4: Wyodrębnij dźwięk z hiperłącza

Jeśli hiperłącze zawiera dźwięk, możemy go wyodrębnić jako tablicę bajtów i zapisać jako plik multimedialny.

```csharp
// Wyodrębnij dźwięk hiperłącza jako tablicę bajtów
byte[] audioData = link.Sound.BinaryData;

// Podaj ścieżkę, w której chcesz zapisać wyodrębniony plik audio
string outMediaPath = Path.Combine(dataDir, "HyperlinkSound.mpg");

// Zapisz wyodrębniony dźwięk do pliku multimedialnego
File.WriteAllBytes(outMediaPath, audioData);
```

Gratulacje! Udało Ci się wyodrębnić dźwięk z hiperłącza w prezentacji PowerPoint przy użyciu Aspose.Slides dla .NET. Teraz możesz używać tego dźwięku w swoich projektach multimedialnych.

## Wniosek

Aspose.Slides for .NET oferuje potężny i przyjazny użytkownikowi sposób wyodrębniania dźwięku z hiperłączy w prezentacjach PowerPoint. Dzięki krokom opisanym w tym przewodniku możesz łatwo ponownie wykorzystać zawartość audio z prezentacji, aby ulepszyć swoje projekty.

## Najczęściej zadawane pytania

### Czy Aspose.Slides dla .NET jest darmową biblioteką?
 Nie, Aspose.Slides dla .NET to biblioteka komercyjna, ale możesz pobrać bezpłatną wersję próbną, aby zapoznać się z jej funkcjami[Tutaj](https://releases.aspose.com/).

### Czy mogę wyodrębnić dźwięk ze starszych formatów programu PowerPoint, np. PPT?
Tak, Aspose.Slides dla .NET obsługuje formaty PPTX i PPT do wyodrębniania dźwięku.

### Czy istnieje forum społecznościowe poświęcone pomocy technicznej Aspose.Slides?
 Oczywiście! Możesz uzyskać pomoc i podzielić się doświadczeniami w[Forum społeczności Aspose.Slides](https://forum.aspose.com/).

### Czy mogę zakupić tymczasową licencję Aspose.Slides na potrzeby krótkoterminowego projektu?
Tak, możesz uzyskać tymczasową licencję na potrzeby krótkoterminowych projektów, odwiedzając stronę[ten link](https://purchase.aspose.com/temporary-license/).

### Czy poza MPG istnieją inne formaty audio obsługiwane przy ekstrakcji?
Tak, Aspose.Slides dla .NET umożliwia ekstrakcję w różnych formatach audio. Możesz przekonwertować audio do preferowanego formatu po ekstrakcji.