---
title: Zastosuj progowanie Bradleya w Aspose.PSD dla .NET
linktitle: Zastosuj progowanie Bradleya
second_title: Aspose.PSD .NET API
description: Dowiedz się, jak krok po kroku ładować pliki PSD, stosować techniki progowania i zapisywać wyniki w różnych formatach, co pozwoli Ci udoskonalić zadania segmentacji obrazu w różnych zastosowaniach.
type: docs
weight: 15
url: /pl/net/tutorials/psd/guide-image-processing/apply-bradley-thresholding/
---
## Wstęp

Witamy w naszym samouczku dotyczącym stosowania techniki Bradley Threshold przy użyciu Aspose.PSD dla .NET. Ta potężna biblioteka umożliwia bezproblemową manipulację plikami Photoshop w aplikacjach .NET. Bradley Thresholding to skuteczna metoda binaryzacji obrazu, która pomaga odróżnić obiekty od ich tła.

## Wymagania wstępne

Zanim rozpoczniesz proces, upewnij się, że spełniasz następujące wymagania wstępne:

-  Aspose.PSD dla biblioteki .NET: Pobierz i zainstaluj najnowszą wersję ze strony[dokumentacja](https://reference.aspose.com/psd/net/).
- Katalog dokumentów: Utwórz katalog roboczy, w którym będziesz przechowywać źródłowy plik PSD i wyjściowy obraz binarny.

## Importuj niezbędne przestrzenie nazw

Rozpocznij swój projekt od zaimportowania odpowiednich przestrzeni nazw, aby uzyskać dostęp do funkcjonalności Aspose.PSD:

```csharp
// Importuj przestrzenie nazw Aspose.PSD
using Aspose.PSD.FileFormats.Psd;
using Aspose.PSD.ImageOptions;
```

## Krok 1: Załaduj obraz źródłowy

Zdefiniuj ścieżkę do katalogu dokumentów, pliku źródłowego PSD i nazwę pliku wyjściowego:

```csharp
// Podaj ścieżkę do katalogu dokumentów
string dataDir = "Your Document Directory";

string sourceFile = Path.Combine(dataDir, "sample.psd");
string outputFile = Path.Combine(dataDir, "binarized_out.png");
```

## Krok 2: Zastosuj próg Bradleya

Następnie wczytaj obraz PSD, wybierz wartość progową, zastosuj próg Bradely'ego i zapisz wyniki:

```csharp
// Załaduj obraz PSD
using (PsdImage image = (PsdImage)Image.Load(sourceFile))
{
    // Ustaw wartość progową (eksperymentuj z tą wartością w razie potrzeby)
    double threshold = 0.15;

    // Binaryzacja obrazu metodą Bradleya
    image.BinarizeBradley(threshold);

    // Zapisz obraz binarny w formacie PNG
    image.Save(outputFile, new PngOptions());
}
```

## Wniosek

Gratulacje! Udało Ci się zaimplementować technikę Bradley Threshold przy użyciu Aspose.PSD dla .NET. Ta metoda może znacznie poprawić segmentację obrazu w różnych aplikacjach, od analizy dokumentów po projektowanie graficzne.

## Najczęściej zadawane pytania

### Czy mogę zastosować próg Bradleya do dowolnego typu obrazu?

Oczywiście! Bradley Thresholding jest wszechstronny i można go stosować do większości typów obrazów w celu poprawy segmentacji.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.PSD?

 Aby uzyskać szczegółową dokumentację i zasoby, odwiedź stronę[Dokumentacja Aspose.PSD](https://reference.aspose.com/psd/net/).

### Czy jest dostępna wersja próbna?

Tak! Możesz wypróbować Aspose.PSD dla .NET za pomocą bezpłatnej wersji próbnej[Tutaj](https://releases.aspose.com/).

### Gdzie mogę uzyskać pomoc dotyczącą Aspose.PSD?

 Aby uzyskać wsparcie społeczności i wziąć udział w dyskusjach, zapoznaj się z[Forum Aspose.PSD](https://forum.aspose.com/c/psd/34).

### Jak mogę zakupić licencję na Aspose.PSD?

 Możesz kupić licencję bezpośrednio[Tutaj](https://purchase.conholdate.com/buy).