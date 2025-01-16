---
title: Wyodrębnij dane skoroszytu z wykresów za pomocą Aspose.Slides dla .NET
linktitle: Wyodrębnij dane skoroszytu z wykresów za pomocą Aspose.Slides dla .NET
second_title: Aspose.Slides .NET API przetwarzania programu PowerPoint
description: Odblokuj potencjał swoich prezentacji PowerPoint, ucząc się, jak odzyskać dane skoroszytu z wykresów za pomocą Aspose.Slides dla .NET. Ten samouczek krok po kroku przeprowadzi Cię przez proces, ułatwiając wyodrębnianie i efektywne wykorzystywanie danych wykresu.
type: docs
weight: 12
url: /pl/net/tutorials/slides/master-additional-chart-features/extract-workbook-data-from-charts/
---
## Wstęp

Praca z prezentacjami PowerPoint może być trudna, szczególnie podczas wyodrębniania cennych danych z osadzonych wykresów. Na szczęście Aspose.Slides dla .NET zapewnia solidne rozwiązanie, które upraszcza ten proces. W tym samouczku krok po kroku pokażemy, jak odzyskać skoroszyt z wykresu w prezentacji PowerPoint.

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnij się, że masz przygotowane następujące elementy:

### Aspose.Slides dla .NET

Musisz mieć zainstalowany Aspose.Slides for .NET w swoim środowisku programistycznym. Jeśli jeszcze tego nie zrobiłeś, możesz pobrać go ze strony internetowej:

[Pobierz Aspose.Slides dla .NET](https://releases.aspose.com/slides/net/)

### Prezentacja PowerPoint

Przygotuj plik prezentacji PowerPoint, zwłaszcza taki, który zawiera wykres z powiązanymi danymi, które chcesz odzyskać.

## Krok 1: Importuj niezbędne przestrzenie nazw

Aby efektywnie pracować z Aspose.Slides, najpierw musisz zaimportować wymagane przestrzenie nazw:

```csharp
using Aspose.Slides;
using Aspose.Slides.Charts;
using Aspose.Slides.Export;
```

## Krok 2: Zdefiniuj katalog dokumentów

Podaj katalog, w którym znajduje się plik prezentacji:

```csharp
string dataDir = "Your Document Directory"; // Dostosuj tę ścieżkę według potrzeb
```

## Krok 3: Załaduj prezentację

Możesz załadować prezentację PowerPoint, włączając odzyskiwanie skoroszytu z pamięci podręcznej wykresu. Oto jak to zrobić:

```csharp
string pptxFile = Path.Combine(dataDir, "YourPresentation.pptx");
string outPptxFile = Path.Combine(RunExamples.OutPath, "RecoveredWorkbook.pptx");

LoadOptions lo = new LoadOptions();
lo.SpreadsheetOptions.RecoverWorkbookFromChartCache = true;

using (Presentation pres = new Presentation(pptxFile, lo))
{
    // Dostęp do danych wykresu i praca z nimi
    // Twój kod będzie tutaj
    pres.Save(outPptxFile, SaveFormat.Pptx);
}
```

 Na tym etapie`LoadOptions` Obiekt umożliwia włączenie odzyskiwania skoroszytu za pomocą`RecoverWorkbookFromChartCache` nieruchomość.

## Krok 4: Pobierz wykres i uzyskaj dostęp do jego skoroszytu

Teraz czas przyjrzeć się wykresowi i pobrać powiązane z nim dane:

```csharp
IChart chart = pres.Slides[0].Shapes[0] as IChart; // Dostosuj indeks według potrzeb
IChartDataWorkbook wb = chart.ChartData.ChartDataWorkbook;

// Teraz możesz pracować z danymi skoroszytu zgodnie ze swoimi wymaganiami
```

Uzyskując dostęp do pierwszego kształtu pierwszego slajdu (który powinien być wykresem), uzyskujesz arkusz danych wykresu i możesz manipulować danymi lub wyodrębniać je według potrzeb.

## Wniosek

W tym samouczku pokazaliśmy, jak skutecznie odzyskać skoroszyt z wykresu w prezentacji PowerPoint przy użyciu Aspose.Slides dla .NET. Postępując zgodnie z tymi krokami, możesz łatwo wyodrębnić i wykorzystać dane wykresu do swoich potrzeb analitycznych.

## Najczęściej zadawane pytania

### Czym jest Aspose.Slides dla .NET?

Aspose.Slides for .NET to zaawansowana biblioteka umożliwiająca programistom programistyczne tworzenie, edytowanie i konwertowanie prezentacji Microsoft PowerPoint.

### Czy mogę wypróbować Aspose.Slides dla .NET przed zakupem?

 Tak! Aspose oferuje bezpłatną wersję próbną Aspose.Slides dla .NET. Możesz ocenić jej możliwości przed dokonaniem zakupu.[Pobierz bezpłatną wersję próbną tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć dokumentację Aspose.Slides dla .NET?

 Możesz uzyskać dostęp do kompleksowej dokumentacji Aspose.Slides dla .NET[Tutaj](https://reference.aspose.com/slides/net/), w tym przykłady i odniesienia do API.

### Jak kupić licencję na Aspose.Slides dla platformy .NET?

 Aby kupić licencję, wejdź na stronę Aspose i skorzystaj z poniższego linku:[Kup Aspose.Slides dla .NET](https://purchase.aspose.com/buy).