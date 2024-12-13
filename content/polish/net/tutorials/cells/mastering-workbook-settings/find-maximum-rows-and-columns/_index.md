---
title: Znajdź maksymalną liczbę wierszy i kolumn w formatach XLS i XLSX
linktitle: Znajdź maksymalną liczbę wierszy i kolumn w formatach XLS i XLSX
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Dowiedz się, jak skutecznie zarządzać dużymi zestawami danych w programie Excel, wykorzystując bibliotekę Aspose.Cells for .NET. Ten przewodnik przedstawia krok po kroku podejście do identyfikacji maksymalnej liczby wierszy i kolumn obsługiwanych przez formaty plików XLS i XLSX.
type: docs
weight: 11
url: /pl/net/tutorials/cells/mastering-workbook-settings/find-maximum-rows-and-columns/
---
## Wstęp

Zarządzanie dużymi zestawami danych w programie Excel może być trudne, zwłaszcza biorąc pod uwagę ograniczenia różnych formatów plików. Ten samouczek przeprowadzi Cię przez korzystanie z biblioteki Aspose.Cells for .NET w celu określenia maksymalnej liczby wierszy i kolumn obsługiwanych przez formaty XLS (Excel 97-2003) i XLSX (Excel 2007 i nowsze). Pod koniec będziesz przygotowany do wydajnego wykonywania zadań związanych z programem Excel.

## Wymagania wstępne

Przed rozpoczęciem upewnij się, że masz następujące rzeczy:

1. [.NET Framework](https://dotnet.microsoft.com/en-us/download) Lub[.NET Core](https://dotnet.microsoft.com/en-us/download) zainstalowany w Twoim systemie.
2. [Aspose.Cells dla .NET](https://releases.aspose.com/cells/net/) biblioteka pobrana i przywoływana w Twoim projekcie (możesz ją również zainstalować za pomocą[Pobierz](https://www.nuget.org/packages/Aspose.Cells/)).

## Importowanie wymaganych pakietów

Dodaj następujące polecenia using na początku pliku C#, aby zaimportować niezbędne pakiety z biblioteki Aspose.Cells:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Krok 1: Maksymalna liczba wierszy i kolumn dla formatu XLS

Zacznijmy od znalezienia maksymalnej liczby wierszy i kolumn obsługiwanych przez format XLS.

```csharp
// Wydrukuj wiadomość o formacie XLS.
Console.WriteLine("Maximum Rows and Columns supported by XLS format:");

// Utwórz skoroszyt w formacie XLS.
Workbook wb = new Workbook(FileFormatType.Excel97To2003);

// Pobierz maksymalną liczbę wierszy i kolumn.
int maxRows = wb.Settings.MaxRow + 1;
int maxCols = wb.Settings.MaxColumn + 1;

// Wyświetl wyniki.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
Console.WriteLine();
```

1. Wydrukuj komunikat informujący, że pracujemy w formacie XLS.
2.  Utwórz`Workbook` wystąpienie dla formatu XLS przy użyciu`FileFormatType.Excel97To2003`.
3.  Uzyskaj maksymalną liczbę wierszy i kolumn za pomocą`wb.Settings.MaxRow` I`wb.Settings.MaxColumn`, dodając 1, ponieważ są to liczby zaczynające się od zera.
4. Wyświetla maksymalną liczbę wierszy i kolumn w konsoli.

## Krok 2: Maksymalna liczba wierszy i kolumn dla formatu XLSX

Następnie przyjrzymy się maksymalnej liczbie wierszy i kolumn obsługiwanych przez format XLSX.

```csharp
// Wydrukuj wiadomość o formacie XLSX.
Console.WriteLine("Maximum Rows and Columns supported by XLSX format:");

// Utwórz skoroszyt w formacie XLSX.
wb = new Workbook(FileFormatType.Xlsx);

// Pobierz maksymalną liczbę wierszy i kolumn.
maxRows = wb.Settings.MaxRow + 1;
maxCols = wb.Settings.MaxColumn + 1;

// Wyświetl wyniki.
Console.WriteLine("Maximum Rows: " + maxRows);
Console.WriteLine("Maximum Columns: " + maxCols);
```

1. Wyświetl komunikat informujący, że pracujemy na formacie XLSX.
2.  Utwórz`Workbook` wystąpienie dla formatu XLSX przy użyciu`FileFormatType.Xlsx`.
3. Pobierz i wyprowadź maksymalną liczbę wierszy i kolumn, jak poprzednio.

## Krok 3: Wyświetlanie komunikatu o powodzeniu

Po wykonaniu kroków należy ogłosić sukces.

```csharp
Console.WriteLine("Execution completed successfully: Maximum Rows and Columns retrieval for both formats.");
```

## Wniosek

W tym samouczku dowiedziałeś się, jak używać biblioteki Aspose.Cells for .NET, aby znaleźć maksymalną liczbę wierszy i kolumn obsługiwanych przez formaty plików XLS i XLSX. Zrozumienie tych ograniczeń jest niezbędne do efektywnego zarządzania danymi w programie Excel, zapewniając, że zestawy danych są zgodne z możliwościami formatu.

## Najczęściej zadawane pytania

### Jaka jest maksymalna liczba wierszy obsługiwana przez format XLS?
Maksymalna liczba wierszy obsługiwana przez format XLS wynosi 65 536.

### Jaka jest maksymalna liczba kolumn obsługiwana przez format XLS?
Maksymalna liczba kolumn obsługiwana przez format XLS wynosi 256.

### Jaka jest maksymalna liczba wierszy obsługiwana przez format XLSX?
Maksymalna liczba wierszy obsługiwana przez format XLSX wynosi 1 048 576.

### Jaka jest maksymalna liczba kolumn obsługiwana przez format XLSX?
Maksymalna liczba kolumn obsługiwanych przez format XLSX wynosi 16 384.

### Czy mogę używać biblioteki Aspose.Cells for .NET z innymi formatami plików Excel?
 Tak, Aspose.Cells dla .NET obsługuje różne formaty plików, w tym XLS, XLSX, ODS i inne. Sprawdź[dokumentacja](https://reference.aspose.com/cells/net/) Aby uzyskać szczegółowe informacje na temat obsługiwanych funkcji i funkcjonalności.