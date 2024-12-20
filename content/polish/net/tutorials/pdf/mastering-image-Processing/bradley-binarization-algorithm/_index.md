---
title: Algorytm binaryzacji Bradleya
linktitle: Algorytm binaryzacji Bradleya
second_title: Aspose.PDF dla .NET API Reference
description: Dowiedz się, jak konwertować strony PDF na wysokiej jakości obrazy binarne TIFF za pomocą algorytmu binaryzacji Bradleya w Aspose.PDF dla .NET. Ten przewodnik krok po kroku zawiera przykład kodu.
type: docs
weight: 30
url: /pl/net/tutorials/pdf/mastering-image-Processing/bradley-binarization-algorithm/
---
## Wstęp

tym samouczku przeprowadzimy Cię przez proces konwersji strony PDF na obraz TIFF przy użyciu algorytmu binaryzacji Bradleya. Aspose.PDF dla .NET upraszcza to zadanie, umożliwiając łatwą automatyzację i usprawnienie przepływów pracy nad dokumentami.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Aspose.PDF dla .NET: Pobierz bibliotekę ze strony[Tutaj](https://releases.aspose.com/pdf/net/).
- Visual Studio (lub dowolne środowisko IDE języka C#).
- Podstawowa znajomość języka C#.
-  Ważne prawo jazdy lub[licencja tymczasowa](https://purchase.aspose.com/temporary-license/) z Aspose.

## Krok 1: Skonfiguruj swój projekt

Najpierw utwórz nowy projekt C# w swoim środowisku IDE i zaimportuj niezbędne przestrzenie nazw:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
```

## Krok 2: Zdefiniuj katalog dokumentów

Podaj ścieżkę do katalogu, w którym znajduje się Twój dokument PDF, a także ścieżki wyjściowe dla obrazów TIFF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Ścieżka do pliku PDF
```

W tym katalogu będą przechowywane zarówno źródłowe pliki PDF, jak i przekonwertowane pliki TIFF.

## Krok 3: Załaduj dokument PDF

Otwórz dokument PDF, który chcesz przekonwertować:

```csharp
Document pdfDocument = new Document(dataDir + "PageToTIFF.pdf");
```

 Zastępować`PageToTIFF.pdf` z nazwą Twojego pliku PDF.

## Krok 4: Określ ścieżki wyjściowe

Zdefiniuj ścieżki wyjściowe dla generowanych plików TIFF:

```csharp
string outputImageFile = dataDir + "resultant_out.tif";
string outputBinImageFile = dataDir + "37116-bin_out.tif";
```

## Krok 5: Ustaw rozdzielczość obrazu

Ustaw rozdzielczość dla obrazów TIFF. Wyższe DPI da lepszą jakość obrazu:

```csharp
Resolution resolution = new Resolution(300);
```

## Krok 6: Skonfiguruj ustawienia TIFF

Skonfiguruj ustawienia obrazu TIFF, w tym kompresję i głębię kolorów:

```csharp
TiffSettings tiffSettings = new TiffSettings
{
    Compression = CompressionType.LZW,
    Depth = Aspose.Pdf.Devices.ColorDepth.Format1bpp
};
```

Użycie 1bpp (1 bit na piksel) przygotowuje obraz do wyjścia binarnego.

## Krok 7: Utwórz urządzenie TIFF

Utwórz urządzenie TIFF, które będzie obsługiwać konwersję:

```csharp
TiffDevice tiffDevice = new TiffDevice(resolution, tiffSettings);
```

## Krok 8: Konwertuj stronę PDF do TIFF

Konwertuj pierwszą stronę pliku PDF na obraz TIFF:

```csharp
tiffDevice.Process(pdfDocument, outputImageFile);
```

## Krok 9: Zastosuj algorytm binaryzacji Bradleya

Teraz zastosuj algorytm Bradleya, aby przekonwertować obraz TIFF w skali szarości na obraz binarny:

```csharp
using (FileStream inStream = new FileStream(outputImageFile, FileMode.Open))
{
    using (FileStream outStream = new FileStream(outputBinImageFile, FileMode.Create))
    {
        tiffDevice.BinarizeBradley(inStream, outStream, 0.1);
    }
}
```

 Ten`BinarizeBradley` metoda przyjmuje dwa strumienie plików (wejście i wyjście) oraz wartość progową. Dostosuj próg w razie potrzeby, aby uzyskać optymalne wyniki.

## Krok 10: Potwierdź pomyślną konwersję

Na koniec potwierdź, że konwersja zakończyła się powodzeniem:

```csharp
Console.WriteLine("Conversion using Bradley algorithm performed successfully!");
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować stronę PDF na obraz TIFF i zastosować algorytm binaryzacji Bradleya przy użyciu Aspose.PDF dla .NET. Ten proces jest niezbędny do archiwizacji dokumentów, OCR i innych profesjonalnych aplikacji. Dzięki wysokiej jakości rozdzielczości i wydajnej kompresji obrazy Twoich dokumentów będą wyraźne i łatwe w zarządzaniu rozmiarem.

## Najczęściej zadawane pytania

### Czym jest algorytm Bradleya?
Algorytm Bradleya to technika binaryzacji, która konwertuje obrazy w skali szarości na obrazy binarne, ustalając próg adaptacyjny dla każdego piksela na podstawie jego otoczenia.

### Czy mogę przekonwertować wiele stron PDF do formatu TIFF za pomocą tej metody?
 Tak, możesz zmodyfikować`Process` metoda umożliwiająca przejście przez wszystkie strony dokumentu w celu konwersji.

### Jaka jest optymalna rozdzielczość przy konwersji plików PDF do formatu TIFF?
W przypadku obrazów wysokiej jakości zaleca się zazwyczaj rozdzielczość 300 DPI, można ją jednak dostosować do indywidualnych potrzeb.

### Co oznacza 1bpp w głębi kolorów?
1bpp (1 bit na piksel) oznacza, że obraz będzie czarno-biały, przy czym każdy piksel będzie albo całkowicie czarny, albo całkowicie biały.

### Czy algorytm Bradleya nadaje się do OCR?
Tak, algorytm Bradleya jest często używany podczas wstępnego przetwarzania OCR, ponieważ poprawia kontrast tekstu w zeskanowanych dokumentach, co przekłada się na większą dokładność rozpoznawania.