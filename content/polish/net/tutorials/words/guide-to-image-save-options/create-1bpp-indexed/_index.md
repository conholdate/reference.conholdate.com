---
title: Utwórz indeks 1Bpp
linktitle: Utwórz indeks 1Bpp
second_title: Aspose.Words API przetwarzania dokumentów
description: W tym przewodniku znajdziesz instrukcje krok po kroku i przykładowy kod, które pomogą Ci efektywnie tworzyć obrazy indeksowane 1 Bpp w celu archiwizacji, drukowania lub oszczędzania miejsca.
type: docs
weight: 10
url: /pl/net/tutorials/words/guide-to-image-save-options/create-1bpp-indexed/
---
## Wstęp

Czy kiedykolwiek musiałeś przekonwertować dokument Word na czarno-biały obraz? Niezależnie od tego, czy chodzi o archiwizację cyfrową, drukowanie, czy po prostu oszczędzanie miejsca, konwersja dokumentów na obraz indeksowany 1Bpp może być niezwykle przydatna. W tym przewodniku przejdziemy przez prostą metodę, aby to osiągnąć przy użyciu Aspose.Words dla .NET. Zaczynajmy!

## Wymagania wstępne

Zanim zagłębisz się w kod, upewnij się, że masz następujące elementy:

-  Aspose.Words dla .NET: Pobierz i zainstaluj bibliotekę z[Tutaj](https://releases.aspose.com/words/net/).
- Środowisko programistyczne .NET: Choć popularnym wyborem jest program Visual Studio, sprawdzi się każde środowisko IDE obsługujące platformę .NET.
- Podstawowa wiedza o języku C#: Znajomość języka C# będzie pomocna, ale postaramy się przedstawić sprawę w prosty sposób.
- Przykładowy dokument Word: Przygotuj dokument do konwersji.

## Krok 1: Importuj niezbędne przestrzenie nazw

Aby użyć Aspose.Words, musisz zaimportować odpowiednie przestrzenie nazw. Jest to niezbędne do uzyskania dostępu do klas i metod wymaganych do manipulacji dokumentami.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 2: Skonfiguruj katalog dokumentów

Podaj ścieżkę do katalogu, w którym znajduje się dokument Word i w którym chcesz zapisać przekonwertowany obraz.

```csharp
// Ścieżka do katalogu dokumentów
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
```

## Krok 3: Załaduj dokument Word

Załaduj dokument Word do`Aspose.Words.Document` obiekt. Ten obiekt pozwala na programową manipulację dokumentem.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 4: Skonfiguruj opcje zapisywania obrazu

 Następnie skonfiguruj`ImageSaveOptions` aby zdefiniować, jak dokument zostanie zapisany jako obraz. Skonfigurujemy go tak, aby zapisywał się w formacie PNG z indeksowanym trybem kolorów 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1), // Konwertuj tylko pierwszą stronę
    ImageColorMode = ImageColorMode.BlackAndWhite, // Ustaw na czarno-biały
    PixelFormat = ImagePixelFormat.Format1bppIndexed // Użyj formatu indeksowanego 1Bpp
};
```

- SaveFormat.Png: Określa, że formatem wyjściowym będzie PNG.
- PageSet(1): Oznacza, że zostanie przekonwertowana tylko pierwsza strona dokumentu.
- ImageColorMode.BlackAndWhite: zapewnia, że obraz będzie czarno-biały.
- ImagePixelFormat.Format1bppIndexed: Ustawia format pikseli na indeksowany 1Bpp, optymalizując przestrzeń.

## Krok 5: Zapisz dokument jako obraz

 Na koniec użyj`Save` metoda`Document` obiekt, aby zapisać przekonwertowany obraz.

```csharp
doc.Save(dataDir + "ConvertedImage.Format1BppIndexed.Png", saveOptions);
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować dokument Word na obraz indeksowany 1Bpp przy użyciu Aspose.Words dla .NET. Ta metoda jest nie tylko wydajna, ale również pomaga tworzyć obrazy o wysokim kontraście, odpowiednie do różnych zastosowań. Możesz swobodnie integrować tę funkcjonalność ze swoimi projektami. Miłego kodowania!

## Najczęściej zadawane pytania

### Czym jest obraz indeksowany 1Bpp?
Obraz indeksowany 1Bpp (1 bit na piksel) to czarno-biały format obrazu, w którym każdy piksel jest reprezentowany przez pojedynczy bit — 0 lub 1. Format ten jest bardzo oszczędny pod względem miejsca, dzięki czemu idealnie nadaje się do archiwizacji.

### Czy mogę przekonwertować wiele stron dokumentu Word jednocześnie?
 Tak! Po prostu zmodyfikuj`PageSet` nieruchomość w`ImageSaveOptions` aby uwzględnić wiele stron lub przekonwertować cały dokument.

### Czy potrzebuję licencji, aby używać Aspose.Words dla .NET?
 Tak, licencja jest wymagana do pełnej funkcjonalności. Możesz uzyskać[tymczasowa licencja tutaj](https://purchase.aspose.com/temporary-license/).

### Do jakich innych formatów obrazów mogę przekonwertować mój dokument Word?
 Aspose.Words obsługuje różne formaty, w tym JPEG, BMP i TIFF. Wystarczy zmienić`SaveFormat`w`ImageSaveOptions` do żądanego formatu.

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Words dla .NET?
 Aby uzyskać pełną dokumentację, odwiedź stronę[Strona dokumentacji Aspose.Words dla .NET](https://reference.aspose.com/words/net/).