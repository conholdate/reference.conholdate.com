---
title: Wdrażanie orientacji strony w arkuszu kalkulacyjnym programu Excel
linktitle: Wdrażanie orientacji strony w arkuszu kalkulacyjnym programu Excel
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Odkryj, jak zwiększyć czytelność i prezentację arkuszy kalkulacyjnych programu Excel, zmieniając orientację strony za pomocą Aspose.Cells dla .NET. Ten przewodnik krok po kroku przeprowadzi Cię przez proces, podając jasny przykład.
type: docs
weight: 18
url: /pl/net/tutorials/cells/mastering-worksheet-page-setup-features/implement-page-orientation-in-excel-worksheet/
---
## Wstęp

Podczas formatowania arkuszy kalkulacyjnych orientacja strony jest kluczowym, ale często pomijanym aspektem. Sposób wyrównania treści może znacząco wpłynąć na czytelność i ogólną estetykę dokumentu. W tym przewodniku przyjrzymy się, jak ustawić orientację strony w arkuszu kalkulacyjnym programu Excel przy użyciu Aspose.Cells dla .NET.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

1. Visual Studio: Upewnij się, że masz go zainstalowanego. Jeśli nie, pobierz go z[Strona pobierania programu Visual Studio](https://visualstudio.microsoft.com/vs/).
2.  Aspose.Cells dla .NET: Pobierz i zainstaluj bibliotekę z[Strona pobierania Aspose](https://releases.aspose.com/cells/net/) . Możesz również zacząć od[bezpłatny okres próbny](https://releases.aspose.com/).
3. Podstawowa znajomość języka C#: Znajomość języka C# będzie pomocna, ponieważ nasze przykłady będą napisane w tym języku.

Teraz gdy wszystko mamy już skonfigurowane, możemy zaimportować niezbędne pakiety.

## Importowanie pakietów

Aby rozpocząć kodowanie, musimy zaimportować bibliotekę Aspose.Cells do naszego projektu. Wykonaj następujące kroki:

### Krok 1: Otwórz program Visual Studio

Uruchom Visual Studio i utwórz nowy projekt C#. Możesz wybrać albo aplikację konsolową albo aplikację Windows Forms, zależnie od swoich preferencji.

### Krok 2: Dodaj odniesienia

W Solution Explorer kliknij prawym przyciskiem myszy swój projekt, wybierz Manage NuGet Packages i wyszukaj bibliotekę Aspose.Cells. Zainstaluj ją, aby uzyskać dostęp do wszystkich jej funkcjonalności.

### Krok 3: Importuj bibliotekę

 W głównym pliku programu (zwykle`Program.cs`), umieść na górze następującą dyrektywę:

```csharp
using System.IO;
using Aspose.Cells;
using System;
```

Dzięki temu uzyskasz dostęp do wszystkich klas i metod udostępnianych przez Aspose.Cells.

Teraz przeanalizujemy proces ustawiania orientacji strony na pionową w arkuszu kalkulacyjnym programu Excel.

## Krok 1: Zdefiniuj katalog dokumentów

Najpierw określ ścieżkę do przechowywania pliku Excel:

```csharp
string dataDir = "Your Document Directory";
```

 Zastępować`"Your Document Directory"` z rzeczywistą ścieżką, taką jak`"C:\\Documents\\"`, w którym chcesz zapisać plik wyjściowy Excela.

## Krok 2: Utwórz obiekt skoroszytu

Następnie utwórz nową instancję skoroszytu. Ten obiekt będzie Twoim obszarem roboczym do manipulowania arkuszami kalkulacyjnymi:

```csharp
Workbook workbook = new Workbook();
```

 Poprzez instancjonowanie`Workbook`, utworzyłeś nowy plik Excela w pamięci.

## Krok 3: Uzyskaj dostęp do pierwszego arkusza kalkulacyjnego

Teraz przejdź do pierwszego arkusza kalkulacyjnego, w którym ustawisz orientację strony:

```csharp
Worksheet worksheet = workbook.Worksheets[0];
```

Ten wiersz pobiera pierwszy arkusz kalkulacyjny ze skoroszytu (należy pamiętać, że arkusze kalkulacyjne mają indeks zerowy).

## Krok 4: Ustaw orientację na pionową

Mając już gotowy arkusz kalkulacyjny, ustaw orientację strony za pomocą następującego wiersza kodu:

```csharp
worksheet.PageSetup.Orientation = PageOrientationType.Portrait;
```

Udało Ci się teraz ustawić arkusz w orientacji pionowej, dzięki czemu Twoja zawartość będzie uporządkowana pionowo.

## Krok 5: Zapisz skoroszyt

Na koniec zapisz zmiany w pliku Excel, aby mieć pewność, że Twoja praca nie zostanie utracona:

```csharp
workbook.Save(dataDir + "PageOrientation_out.xls");
```

 Zapisuje skoroszyt pod nazwą`PageOrientation_out.xls` w określonym katalogu.

## Wniosek

Gratulacje! Nauczyłeś się, jak zaimplementować orientację strony w arkuszu kalkulacyjnym za pomocą Aspose.Cells dla .NET. To prosty proces, który może zwiększyć czytelność i profesjonalizm Twoich arkuszy kalkulacyjnych.

## Najczęściej zadawane pytania

### Czy Aspose.Cells jest darmowy?

 Aspose.Cells to płatna biblioteka, ale możesz zacząć od[bezpłatny okres próbny](https://releases.aspose.com/) aby poznać jego funkcje.

### Czy mogę również zmienić orientację strony na poziomą?

 Oczywiście! Po prostu zamień`PageOrientationType.Portrait` z`PageOrientationType.Landscape` w twoim kodzie.

### Jakie wersje platformy .NET obsługuje Aspose.Cells?

Aspose.Cells obsługuje wiele wersji platformy .NET, w tym .NET Framework, .NET Core i .NET Standard.

### Jak mogę uzyskać dalszą pomoc, jeśli napotkam problemy?

 Aby uzyskać pomoc, odwiedź stronę[Forum wsparcia Aspose](https://forum.aspose.com/c/cells/9), gdzie społeczność i zespół mogą Ci pomóc.

### Gdzie mogę znaleźć pełną dokumentację?

 Pełną dokumentację Aspose.Cells można znaleźć[Tutaj](https://reference.aspose.com/cells/net/).