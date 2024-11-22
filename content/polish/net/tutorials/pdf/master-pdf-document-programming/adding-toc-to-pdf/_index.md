---
title: Dodawanie spisu treści do dokumentu PDF
linktitle: Dodawanie spisu treści do dokumentu PDF
second_title: Aspose.PDF dla .NET API Reference
description: W tym samouczku pokazano, jak dodać spis treści (TOC) do dokumentu PDF przy użyciu Aspose.Pdf dla platformy .NET.
type: docs
weight: 40
url: /pl/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Wstęp

Utworzenie spisu treści (TOC) w dokumencie PDF może znacznie poprawić jego nawigację i dostępność. W tym przewodniku pokażemy, jak dodać spis treści do pliku PDF za pomocą Aspose.Pdf dla .NET.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz następujące rzeczy:

1.   Aspose.PDF dla .NET: Pobierz i zainstaluj najnowszą wersję z[Tutaj](https://releases.aspose.com/pdf/net/).
2.  Środowisko programistyczne: skonfiguruj środowisko programistyczne .NET, np. Visual Studio.
3.   Licencja: W razie potrzeby poproś o tymczasową licencję; odwiedź stronę[Strona licencjonowania Aspose.Pdf](https://asposepdf.com/developers) Aby uzyskać więcej informacji.

Importowanie niezbędnych bibliotek

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Krok 1: Załaduj dokument PDF

Załaduj istniejący plik PDF, do którego chcesz dodać spis treści. Podaj ścieżkę do katalogu dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Krok 2: Wstaw nową stronę dla spisu treści

Wstaw nową stronę na początku dokumentu PDF. Ta strona będzie służyć jako spis treści (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Krok 3: Utwórz obiekt informacyjny TOC

Utwórz obiekt, który będzie reprezentował informacje TOC. Dodaj tytuł i link do niego, aby ułatwić nawigację.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Krok 4: Zdefiniuj elementy spisu treści

Zdefiniuj elementy (lub nagłówki), które będą wyświetlane w spisie treści. Te elementy mogą pomóc czytelnikom w nawigacji do określonych sekcji dokumentu.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Krok 5: Utwórz nagłówki spisu treści

Utwórz nagłówki dla pierwszych dwóch elementów w spisie treści. Nagłówki te będą linkować do odpowiednich stron.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Krok 6: Zapisz plik PDF ze spisem treści

Na koniec zapisz zaktualizowany plik PDF.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Wiadomość potwierdzająca

Wyświetl komunikat potwierdzający, aby poinformować użytkownika, że proces został zakończony.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Wniosek

Dzięki Aspose.PDF dla .NET dodawanie spisu treści do pliku PDF jest nie tylko łatwe, ale również konfigurowalne. Niezależnie od tego, czy potrzebujesz utworzyć proste linki nawigacyjne, czy złożone struktury, to narzędzie Ci pomoże. Więc następnym razem, gdy będziesz pracować nad długim plikiem PDF, nie zapomnij dodać spisu treści, aby nadać mu profesjonalny charakter.

## Najczęściej zadawane pytania

### Czy mogę dostosować wygląd spisu treści w pliku Aspose.PDF?

Tak, możesz w pełni dostosować wygląd spisu treści, łącznie ze stylem, rozmiarem i wyrównaniem czcionki.

### Jak dodać podtytuły do spisu treści?

 Możesz dodać podtytuły, dostosowując`Heading` poziom (np.`Heading(2)`).

### Czy istnieje możliwość automatycznej aktualizacji spisu treści w przypadku zmian w dokumencie?

Nie, spis treści nie zostanie automatycznie zaktualizowany. Będziesz musiał go utworzyć ponownie, jeśli struktura dokumentu ulegnie zmianie.

### Czy mogę łączyć wpisy spisu treści z dokumentami zewnętrznymi?

Tak, możesz używać hiperłączy w celu łączenia wpisów w spisie treści z zewnętrznymi plikami PDF lub adresami URL.

### Czy Aspose.PDF obsługuje wielopoziomowe spisy treści?

Tak, Aspose.PDF obsługuje wielopoziomowe spisy treści w przypadku złożonych dokumentów z podsekcjami.
