---
title: Ochrona wierszy w arkuszu kalkulacyjnym za pomocą Aspose.Cells
linktitle: Ochrona wierszy w arkuszu kalkulacyjnym za pomocą Aspose.Cells
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Dowiedz się, jak zabezpieczyć poufne informacje w arkuszach kalkulacyjnych programu Excel, chroniąc określone wiersze za pomocą Aspose.Cells dla .NET. Ten kompleksowy samouczek obejmuje wszystko, od konfiguracji środowiska.
type: docs
weight: 18
url: /pl/net/tutorials/cells/mastering-worksheet-security/protecting-rows/
---
## Wstęp

Praca z plikami Excela programowo często wymaga nie tylko manipulacji danymi, ale także ich ochrony. Ochrona określonych wierszy w arkuszu kalkulacyjnym może mieć kluczowe znaczenie dla ochrony poufnych informacji lub zapobiegania przypadkowym edycjom. W tym samouczku omówimy, jak chronić wiersze w arkuszu kalkulacyjnym Excela za pomocą Aspose.Cells dla .NET. Przeprowadzimy Cię przez niezbędne kroki, od konfiguracji środowiska po implementację funkcji ochrony wierszy w prosty sposób.

## Wymagania wstępne
Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

1.  Aspose.Cells dla .NET: Pobierz i zainstaluj z[Strona pobierania Aspose Cells](https://releases.aspose.com/cells/net/).
2. Visual Studio lub dowolne IDE .NET: Potrzebujesz środowiska programistycznego. Zalecane jest Visual Studio, ale wystarczy dowolne IDE zgodne z .NET.
3. Podstawowa wiedza o języku C#: Znajomość programowania w języku C# pomoże Ci śledzić przykładowy kod i modyfikować go w razie potrzeby.
4.  Dokumentacja API Aspose.Cells: Przejrzyj[Dokumentacja Aspose.Cells dla .NET](https://reference.aspose.com/cells/net/) aby uzyskać przegląd struktury i metod klasy.

Gdy już przygotujesz wszystkie wymagania wstępne, możemy przejść do realizacji.

## Importuj niezbędne pakiety
Zacznij od zaimportowania wymaganych pakietów w swoim projekcie C#. Te biblioteki są niezbędne do interakcji z plikami Excel.

```csharp
using System.IO;
using Aspose.Cells;
```

## Krok 1: Utwórz nowy skoroszyt i arkusz kalkulacyjny
Przed zastosowaniem jakichkolwiek ustawień ochrony utwórz nowy skoroszyt i wybierz arkusz, z którym chcesz pracować.

```csharp
// Zdefiniuj ścieżkę do katalogu dokumentów.
string dataDir = "Your Document Directory";
// Utwórz katalog, jeśli nie istnieje.
if (!Directory.Exists(dataDir))
    Directory.CreateDirectory(dataDir);

// Utwórz nowy skoroszyt i wybierz pierwszy arkusz.
Workbook wb = new Workbook();
Worksheet sheet = wb.Worksheets[0];
```

## Krok 2: Zdefiniuj obiekty Style i StyleFlag
Zdefiniuj styl i obiekty flagi stylu, które umożliwią Ci modyfikację właściwości komórki, na przykład ich blokowanie lub odblokowywanie.

```csharp
// Zdefiniuj styl i obiekty flagi stylu.
Style style;
StyleFlag flag;
```

## Krok 3: Odblokuj wszystkie kolumny w arkuszu kalkulacyjnym
Domyślnie wszystkie komórki w arkuszu kalkulacyjnym Excel są zablokowane. Aby chronić tylko określone wiersze, najpierw odblokuj wszystkie kolumny.

```csharp
// Przejdź przez wszystkie kolumny i odblokuj je.
for (int i = 0; i <= 255; i++)
{
    style = sheet.Cells.Columns[i].Style;
    style.IsLocked = false;
    flag = new StyleFlag { Locked = true };
    sheet.Cells.Columns[i].ApplyStyle(style, flag);
}
```

## Krok 4: Zablokuj określone wiersze
Teraz zablokuj wiersze, które chcesz chronić. W tym przykładzie zablokujemy pierwszy wiersz.

```csharp
// Zablokuj pierwszy rząd.
style = sheet.Cells.Rows[0].Style;
style.IsLocked = true;
flag = new StyleFlag { Locked = true };
sheet.Cells.ApplyRowStyle(0, style, flag);
```

Możesz powtórzyć ten krok dla każdego kolejnego wiersza, który chcesz zablokować.

## Krok 5: Zabezpiecz arkusz
Po zablokowaniu niezbędnych wierszy nadszedł czas na ochronę arkusza kalkulacyjnego. Zapobiegnie to modyfikacjom zablokowanych wierszy, chyba że ochrona zostanie usunięta.

```csharp
// Chroń arkusz.
sheet.Protect(ProtectionType.All);
```

## Krok 6: Zapisz skoroszyt
Na koniec zapisz skoroszyt ze zastosowanymi zmianami. Możesz wybierać spośród różnych formatów, takich jak Excel 97-2003 lub nowsze wersje.

```csharp
// Zapisz plik Excela.
wb.Save(dataDir + "output.out.xls", SaveFormat.Excel97To2003);
```

## Wniosek
Gratulacje! Udało Ci się nauczyć, jak chronić wiersze w arkuszu kalkulacyjnym programu Excel za pomocą Aspose.Cells dla .NET. Wykonując te kroki, możesz odblokować lub zablokować wiersze lub kolumny w razie potrzeby i zastosować ochronę, aby zachować integralność danych.

## Najczęściej zadawane pytania
### Jak mogę chronić wiele wierszy jednocześnie?
Można przechodzić przez wiele indeksów wierszy i stosować styl blokowania do każdego z nich osobno.

### Czy mogę ustawić hasło zabezpieczające arkusz?
 Tak, możesz przekazać hasło`sheet.Protect()` metoda wymuszania ochrony hasłem.

### Czy mogę odblokować konkretne komórki zamiast całych kolumn?
Tak, możesz odblokować poszczególne komórki, modyfikując ich właściwości stylu, zamiast odblokowywać całe kolumny.

### Co się stanie, jeśli spróbuję edytować chroniony wiersz?
Gdy wiersz jest chroniony, program Excel uniemożliwi edycję zablokowanych komórek, chyba że arkusz jest niechroniony.

### Czy mogę chronić konkretne zakresy w wierszu?
 Tak! Możesz zablokować poszczególne zakresy w rzędzie, ustawiając`IsLocked` właściwość dla określonych komórek w tym zakresie.