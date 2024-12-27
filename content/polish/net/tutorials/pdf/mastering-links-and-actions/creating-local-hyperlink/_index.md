---
title: Tworzenie lokalnego hiperłącza w pliku PDF
linktitle: Tworzenie lokalnego hiperłącza w pliku PDF
second_title: Aspose.PDF dla .NET API Reference
description: Dowiedz się, jak ulepszyć nawigację w dokumentach PDF, tworząc lokalne hiperłącza za pomocą Aspose.PDF dla .NET. Ten samouczek krok po kroku przeprowadzi Cię przez cały proces.
type: docs
weight: 40
url: /pl/net/tutorials/pdf/mastering-links-and-actions/creating-local-hyperlink/
---
## Wstęp

W tym przewodniku przeprowadzimy Cię przez proces tworzenia lokalnych hiperłączy w pliku PDF przy użyciu Aspose.PDF dla .NET. Przedstawimy każdy krok w sposób przejrzysty, zapewniając, że nawet jeśli jesteś początkujący w manipulowaniu plikami PDF, będziesz w stanie bez problemu nadążyć.

## Wymagania wstępne

Zanim zagłębisz się w kod, upewnij się, że masz następujące elementy:

1.  Visual Studio: Pobierz ze strony[Witryna internetowa Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.PDF dla .NET: Pobierz bibliotekę za pomocą[Strona internetowa Aspose](https://releases.aspose.com/pdf/net/). Ta biblioteka zapewnia bogaty zestaw funkcji do manipulacji plikami PDF.
3. Podstawowa znajomość języka C#: Znajomość programowania w języku C# będzie pomocna, ale nie martw się – wyjaśnimy kod linijka po linijce.
4. .NET Framework: Upewnij się, że masz zainstalowany .NET Framework na swoim komputerze. Sprawdź wymagania w pliku Aspose.PDF[dokumentacja](https://reference.aspose.com/pdf/net/).

Mając te wymagania wstępne, możesz się nauczyć, jak tworzyć lokalne hiperłącza w dokumentach PDF!

## Importowanie wymaganych pakietów

Teraz, gdy wszystko jest już skonfigurowane, czas zaimportować niezbędne pakiety do projektu C#.

### Otwórz swój projekt

Otwórz istniejący projekt .NET lub utwórz nowy w Visual Studio. Jeśli zaczynasz od nowa, wybierz „Utwórz nowy projekt” na ekranie startowym.

### Dodaj odniesienie do Aspose.PDF

 Kliknij prawym przyciskiem myszy „Dependencies” w folderze projektu w Solution Explorer. Wybierz „Manage NuGet Packages”, wyszukaj`Aspose.PDF`i zainstaluj najnowszą dostępną wersję. Dzięki temu uzyskasz wszystkie narzędzia potrzebne do tworzenia i manipulowania plikami PDF.

### Importuj przestrzenie nazw

Na górze pliku .cs dodaj następujące dyrektywy using:

```csharp
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

Dyrektywy te umożliwiają bezproblemowy dostęp do funkcji biblioteki.

Omówmy proces tworzenia lokalnych hiperłączy w kilku prostych krokach.

## Krok 1: Skonfiguruj instancję dokumentu

 Utwórz nową instancję`Document` klasa, reprezentująca plik PDF, z którym będziesz pracować.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY"; // Ustaw katalog dokumentów
Document doc = new Document(); // Utwórz instancję dokumentu
```

 Zastępować`"YOUR_DOCUMENT_DIRECTORY"` z rzeczywistą ścieżką w systemie, gdzie zostanie zapisany plik PDF.

## Krok 2: Dodaj stronę do dokumentu

Następnie dodaj stronę do dokumentu PDF.

```csharp
Page page = doc.Pages.Add(); // Dodaj nową stronę
```

Ten wiersz dodaje nową stronę do dokumentu, na której zostanie umieszczona cała Twoja treść.

## Krok 3: Utwórz fragment tekstu

Teraz utwórzmy fragment tekstu, który będzie pełnić rolę klikalnego linku.

```csharp
Aspose.Pdf.Text.TextFragment text = new Aspose.Pdf.Text.TextFragment("link page number test to page 7"); // Utwórz fragment tekstu
```

 Ten`TextFragment` wyświetli tekst, w który użytkownicy mogą kliknąć.

## Krok 4: Utwórz lokalne hiperłącze

Teraz utwórz lokalny hiperłącze kierujące do strony 7.

```csharp
LocalHyperlink link = new LocalHyperlink(); // Utwórz lokalne hiperłącze
link.TargetPageNumber = 7; // Ustaw stronę docelową dla linku
text.Hyperlink = link; // Ustaw hiperłącze dla fragmentu tekstu
```

 Ten`LocalHyperlink` Klasa umożliwia określenie numeru strony docelowej dla hiperłącza.

## Krok 5: Dodaj fragment tekstu do strony

Dodaj klikalny tekst do utworzonej strony.

```csharp
page.Paragraphs.Add(text); // Dodaj fragment tekstu do strony
```

Ten wiersz dodaje Twój tekst do zbioru akapitów na stronie.

## Krok 6: Utwórz kolejny fragment tekstu (opcjonalnie)

Dodajmy kolejny hiperłącze, aby powrócić do strony 1.

```csharp
TextFragment textBack = new TextFragment("Link to page 1"); // Utwórz nowy fragment tekstu
textBack.IsInNewPage = true; // Wskaż, że powinno to być na nowej stronie
```

## Krok 7: Skonfiguruj drugie lokalne łącze hipertekstowe

Utwórz kolejny lokalny hiperłącze dla strony 1.

```csharp
Aspose.Pdf.LocalHyperlink linkBack = new Aspose.Pdf.LocalHyperlink(); // Utwórz kolejny lokalny hiperłącze
linkBack.TargetPageNumber = 1; // Ustaw stronę docelową dla drugiego hiperłącza
textBack.Hyperlink = linkBack; // Ustaw hiperłącze dla drugiego fragmentu tekstu
```

## Krok 8: Dodaj drugi fragment tekstu do nowej strony

Dodaj drugi fragment tekstu do odpowiedniej strony.

```csharp
Page newPage = doc.Pages.Add(); // Dodaj nową stronę dla drugiego linku
newPage.Paragraphs.Add(textBack); // Dodaj fragment tekstu do nowej strony
```

## Krok 9: Zapisz dokument

Na koniec zapisz dokument.

```csharp
dataDir = dataDir + "CreateLocalHyperlink_out.pdf"; // Określ nazwę pliku wyjściowego
doc.Save(dataDir); // Zapisz zaktualizowany dokument
Console.WriteLine("\nLocal hyperlink created successfully.\nFile saved at " + dataDir);
```

 Ten wiersz łączy ścieżkę do katalogu z nazwą pliku i`Save()` Metoda zapisuje Twój dokument.

## Wniosek

Tworzenie lokalnych hiperłączy w plikach PDF przy użyciu Aspose.PDF dla .NET to praktyczna funkcja, która usprawnia nawigację i doświadczenie użytkownika. Teraz masz wiedzę, aby poprowadzić czytelników bezpośrednio do potrzebnych im informacji, dzięki czemu Twoje pliki PDF będą bardziej interaktywne i przyjazne dla użytkownika.

## Najczęściej zadawane pytania

### Czym jest Aspose.PDF dla .NET?
Aspose.PDF dla platformy .NET to biblioteka umożliwiająca programistom tworzenie, modyfikowanie i konwertowanie dokumentów PDF programowo przy użyciu środowiska .NET.

### Czy mogę tworzyć hiperłącza do zewnętrznych stron internetowych?
Tak, Aspose.PDF oprócz lokalnych hiperłączy w pliku PDF obsługuje również tworzenie hiperłączy do zewnętrznych adresów URL.

### Czy istnieje bezpłatna wersja próbna Aspose.PDF?
 Oczywiście! Możesz uzyskać dostęp do bezpłatnej wersji próbnej z[Strona internetowa Aspose](https://releases.aspose.com/).

### Jakie języki programowania obsługuje Aspose?
Aspose oferuje biblioteki dla różnych języków programowania, w tym Java, C++i Python, między innymi.

### W jaki sposób mogę uzyskać wsparcie dotyczące produktów Aspose?
 Możesz szukać wsparcia poprzez[Forum Aspose](https://forum.aspose.com/c/pdf/10).