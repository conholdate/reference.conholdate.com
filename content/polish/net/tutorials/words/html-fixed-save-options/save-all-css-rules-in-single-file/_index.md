---
title: Zapisz wszystkie reguły CSS w jednym pliku
linktitle: Zapisz wszystkie reguły CSS w jednym pliku
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak używać Aspose.Words dla .NET, aby zapisać wszystkie reguły CSS w jednym pliku podczas zapisywania dokumentów za pomocą HtmlFixedSaveOptions. Postępuj zgodnie z tym szczegółowym samouczkiem, aby uzyskać wskazówki krok po kroku.
type: docs
weight: 10
url: /pl/net/tutorials/words/html-fixed-save-options/save-all-css-rules-in-single-file/
---
## Wstęp

Czy kiedykolwiek zmagałeś się z chaotyczną tablicą reguł CSS podczas konwersji dokumentów Word na HTML? Nie jesteś sam! Na szczęście Aspose.Words dla .NET oferuje potężną funkcję, która pozwala skonsolidować wszystkie reguły CSS w jednym pliku. To nie tylko oczyszcza kod, ale także upraszcza przepływ pracy. Wyruszmy w podróż w kierunku czystszego, bardziej wydajnego wyjścia HTML!

## Wymagania wstępne

Zanim przejdziemy do kodowania, upewnij się, że masz następujące rzeczy:

1.  Aspose.Words dla .NET: Pobierz bibliotekę z[Tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne .NET: środowisko takie jak Visual Studio idealnie nadaje się do tworzenia oprogramowania.
3. Podstawowa wiedza o języku C#: Znajomość języka C# pomoże Ci poruszać się po kodzie.
4. Dokument Word: Przygotuj plik .docx do konwersji.

## Importuj przestrzenie nazw

Po pierwsze, zaimportujmy niezbędne przestrzenie nazw do projektu C#. Pozwoli nam to na łatwy dostęp do funkcjonalności Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Podzielmy ten proces na łatwiejsze do opanowania kroki, aby zapewnić płynną konwersję.

## Krok 1: Skonfiguruj katalog dokumentów

Najpierw ustal ścieżkę katalogu, w którym znajduje się dokument Word i w którym zostanie zapisany przekonwertowany kod HTML.

```csharp
// Zdefiniuj ścieżkę do katalogu dokumentów
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Krok 2: Załaduj dokument Word

 Następnie załaduj dokument Word za pomocą`Document` klasa z biblioteki Aspose.Words.

```csharp
// Załaduj dokument Word
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 3: Skonfiguruj opcje zapisywania HTML

 Teraz skonfigurujmy opcje zapisywania HTML. Chcemy włączyć funkcję, która konsoliduje wszystkie reguły CSS w jednym pliku, ustawiając`SaveFontFaceCssSeparately` Do`false`.

```csharp
// Skonfiguruj opcje zapisywania HTML, aby zapisać wszystkie reguły CSS w jednym pliku
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Krok 4: Konwertuj dokument do formatu HTML

Na koniec zapisz dokument jako plik HTML z określonymi opcjami. Dzięki temu wszystkie reguły CSS będą uporządkowane w jednym pliku.

```csharp
// Konwertuj dokument do formatu HTML
doc.Save(dataDir + "ConvertedDocument.html", saveOptions);
```

## Wniosek

Gratulacje! Za pomocą zaledwie kilku linijek kodu udało Ci się przekonwertować dokument Word na HTML, zapewniając, że wszystkie reguły CSS są starannie skompilowane w jednym pliku. Takie podejście upraszcza zarządzanie CSS i zwiększa łatwość obsługi dokumentów HTML. Następnym razem, gdy będziesz musiał przekonwertować dokument Word, będziesz mieć usprawniony proces na wyciągnięcie ręki!

## Najczęściej zadawane pytania

### Dlaczego powinienem używać jednego pliku CSS do wydruku w formacie HTML?
Pojedynczy plik CSS upraszcza zarządzanie stylami, dzięki czemu kod HTML jest bardziej przejrzysty i łatwiejszy w utrzymaniu.

### Czy w razie potrzeby mogę oddzielić reguły CSS dotyczące kroju czcionki?
 Absolutnie! Ustawiając`SaveFontFaceCssSeparately` Do`true`, możesz oddzielić reguły CSS dotyczące kroju czcionki do osobnego pliku.

### Czy korzystanie z Aspose.Words dla .NET jest bezpłatne?
 Aspose.Words oferuje bezpłatną wersję próbną dostępną do pobrania[Tutaj](https://releases.aspose.com/) . Aby kontynuować użytkowanie, rozważ zakup licencji[Tutaj](https://purchase.aspose.com/buy).

### Do jakich innych formatów można konwertować za pomocą Aspose.Words for .NET?
Aspose.Words obsługuje różne formaty, w tym PDF, TXT oraz formaty obrazów JPEG i PNG.

### Gdzie mogę znaleźć więcej materiałów na temat Aspose.Words dla .NET?
 Aby uzyskać kompleksowe przewodniki i odniesienia do interfejsu API, zapoznaj się z[dokumentacja](https://reference.aspose.com/words/net/).
