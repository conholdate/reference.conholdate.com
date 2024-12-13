---
title: Implementacja nagłówka i stopki za pomocą Aspose.Cells dla .NET
linktitle: Implementacja nagłówka i stopki za pomocą Aspose.Cells dla .NET
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Dowiedz się, jak podnieść poziom swoich dokumentów Excela, programowo dostosowując nagłówki i stopki za pomocą Aspose.Cells dla .NET. Ten kompleksowy przewodnik przeprowadzi Cię przez każdy krok — od konfiguracji skoroszytu po dynamiczne wstawianie nazwy arkusza.
type: docs
weight: 22
url: /pl/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-header-footer/
---
## Wstęp

Nagłówki i stopki są niezbędnymi elementami arkuszy kalkulacyjnych programu Excel, dostarczającymi krytycznych informacji kontekstowych, takich jak nazwy plików, daty i numery stron. Niezależnie od tego, czy automatyzujesz raporty, czy generujesz pliki dynamiczne, Aspose.Cells for .NET upraszcza proces dostosowywania nagłówków i stopek programowo. Ten przewodnik oferuje podejście krok po kroku, aby ulepszyć pliki programu Excel za pomocą dopracowanych i profesjonalnych nagłówków i stopek.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

1.  Aspose.Cells dla .NET: Pobierz i zainstaluj ze strony[Tutaj](https://releases.aspose.com/cells/net/).
2. Konfiguracja środowiska IDE: Użyj programu Visual Studio lub preferowanego środowiska IDE z platformą .NET Framework.
3.  Licencja: Zacznij od bezpłatnego okresu próbnego, ale rozważ uzyskanie pełnej lub tymczasowej licencji na pełną funkcjonalność. Możesz[zdobądź tymczasową licencję](https://purchase.aspose.com/temporary-license/).

## Importowanie wymaganych pakietów

Zacznij od zaimportowania niezbędnych przestrzeni nazw do swojego projektu:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Dzięki temu uzyskasz dostęp do klas i metod niezbędnych do pracy z nagłówkami, stopkami i innymi funkcjonalnościami programu Excel w Aspose.Cells.

## Krok 1: Utwórz skoroszyt i uzyskaj dostęp do ustawień strony

Zacznij od utworzenia nowego skoroszytu i uzyskania dostępu do ustawień strony arkusza. Tutaj zmodyfikujesz ustawienia nagłówka i stopki.

```csharp
// Zdefiniuj ścieżkę do zapisania dokumentu
string dataDir = "Your Document Directory";

// Utwórz obiekt skoroszytu
Workbook excel = new Workbook();
```

 Tutaj,`Workbook` Obiekt reprezentuje Twój plik Excel.`PageSetup` arkusza kalkulacyjnego umożliwia dostosowanie nagłówków i stopek.

## Krok 2: Uzyskaj dostęp do właściwości arkusza kalkulacyjnego i ustawień strony

 Każdy arkusz w Aspose.Cells ma`PageSetup` właściwość, która reguluje funkcje układu, w tym nagłówki i stopki. Uzyskaj`PageSetup` obiekt dla twojego arkusza kalkulacyjnego:

```csharp
// Uzyskaj odniesienie do PageSetup pierwszego arkusza kalkulacyjnego
PageSetup pageSetup = excel.Worksheets[0].PageSetup;
```

 Teraz,`pageSetup` zawiera ustawienia wymagane do dostosowania nagłówków i stopek.

## Krok 3: Ustaw lewą sekcję nagłówka

Nagłówki składają się z trzech sekcji: lewej, środkowej i prawej. Zacznijmy od ustawienia lewej sekcji, aby wyświetlała nazwę arkusza kalkulacyjnego.

```csharp
// Ustaw nazwę arkusza roboczego w lewej części nagłówka
pageSetup.SetHeader(0, "&A");
```

 Używanie`&A`dynamicznie wyświetla nazwę arkusza kalkulacyjnego, co jest szczególnie przydatne w przypadku skoroszytów zawierających wiele arkuszy.

## Krok 4: Dodaj datę i godzinę do środka nagłówka

Następnie dodaj bieżącą datę i godzinę do środkowej części nagłówka, stosując niestandardową czcionkę w celu jej wystylizowania.

```csharp
// Ustaw datę i godzinę w środkowej części nagłówka za pomocą pogrubionej czcionki
pageSetup.SetHeader(1, "&\"Times New Roman,Bold\"&D-&T");
```

W tym wierszu:
- `&D` wstawia bieżącą datę.
- `&T` wstawia aktualny czas.
- `"Times New Roman,Bold"` stosuje pogrubioną czcionkę Times New Roman.

## Krok 5: Wyświetl nazwę pliku w prawej części nagłówka

Aby ukończyć nagłówek, wyświetl nazwę pliku po prawej stronie, używając określonego rozmiaru czcionki.

```csharp
// Wyświetl nazwę pliku w prawej części nagłówka z niestandardowym rozmiarem czcionki
pageSetup.SetHeader(2, "&\"Times New Roman,Bold\"&12&F");
```

 Tutaj,`&F` reprezentuje nazwę pliku i`&12` ustawia rozmiar czcionki na 12.

## Krok 6: Dodaj niestandardowy tekst do sekcji lewej stopki

Teraz ustawmy lewą sekcję stopki, dodając niestandardowy tekst i określony styl czcionki.

```csharp
// Dodaj niestandardowy tekst ze stylem czcionki do lewej części stopki
pageSetup.SetFooter(0, "Hello World! &\"Courier New\"&14 123");
```

 tym przykładzie tekst`123` jest napisana czcionką „Courier New” o rozmiarze 14, reszta stopki pozostała w domyślnej czcionce.

## Krok 7: Wstaw numer strony na środku stopki

Umieszczenie numerów stron w stopce ułatwia czytelnikom śledzenie dokumentów wielostronicowych.

```csharp
// Wstaw numer strony w środkowej części stopki
pageSetup.SetFooter(1, "&P");
```

 Ten`&P` Kod dodaje numer bieżącej strony do środkowej części stopki.

## Krok 8: Wyświetl całkowitą liczbę stron w prawej stopce

Uzupełnij stopkę, wyświetlając w prawej sekcji całkowitą liczbę stron.

```csharp
// Wyświetl całkowitą liczbę stron w prawej części stopki
pageSetup.SetFooter(2, "&N");
```

 Ten`&N` Kod podaje całkowitą liczbę stron, informując czytelników o długości dokumentu.

## Krok 9: Zapisz skoroszyt

Na koniec zapisz skoroszyt, aby wygenerować plik Excela z dostosowanymi nagłówkami i stopkami.

```csharp
// Zapisz skoroszyt
excel.Save(dataDir + "SetHeadersAndFooters_out.xls");
```

Ten wiersz zapisuje plik z wprowadzonymi zmianami.

## Wniosek

Dostosowywanie nagłówków i stopek w arkuszach kalkulacyjnych programu Excel zwiększa profesjonalizm dokumentów. Dzięki Aspose.Cells dla .NET możesz łatwo kontrolować te elementy, od wyświetlania nazw arkuszy kalkulacyjnych po wstawianie niestandardowego tekstu, dat, godzin i dynamicznych numerów stron. Teraz, gdy poznałeś już kroki, możesz podnieść poziom swoich projektów automatyzacji programu Excel.

## Najczęściej zadawane pytania

### Czy mogę używać różnych czcionek w różnych sekcjach nagłówka i stopki?
Tak, Aspose.Cells pozwala na określenie unikalnych czcionek dla każdej sekcji nagłówka i stopki.

### Jak usunąć nagłówki i stopki?
 Wyczyść nagłówki i stopki, ustawiając ich tekst na pusty ciąg za pomocą`SetHeader` Lub`SetFooter`.

### Czy mogę wstawiać obrazy do nagłówków i stopek za pomocą Aspose.Cells dla .NET?
Obecnie Aspose.Cells obsługuje głównie tekst w nagłówkach i stopkach. Obrazy mogą wymagać alternatywnych metod, takich jak wstawianie ich bezpośrednio do arkusza kalkulacyjnego.

### Czy Aspose.Cells obsługuje dynamiczne dane w nagłówkach i stopkach?  
 Tak, możesz używać różnych kodów dynamicznych (takich jak`&D`na datę lub`&P` (w celu uzyskania numeru strony) w celu dodania dynamicznej zawartości.

### Jak mogę dostosować wysokość nagłówka lub stopki?  
 Aspose.Cells zapewnia opcje w ramach`PageSetup` Klasa umożliwiająca dostosowanie marginesów nagłówka i stopki, co daje Ci kontrolę nad odstępami.