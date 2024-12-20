---
title: Przenoszenie formularzy użytkownika VBA i makr między skoroszytami programu Excel
linktitle: Przenoszenie formularzy użytkownika VBA i makr między skoroszytami programu Excel
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Odblokuj moc automatyzacji programu Excel dzięki temu kompleksowemu przewodnikowi na temat przenoszenia formularzy użytkownika VBA i makr między skoroszytami przy użyciu Aspose.Cells dla .NET. Idealne zarówno dla początkujących, jak i doświadczonych programistów.
type: docs
weight: 11
url: /pl/net/tutorials/cells/mastering-workbook-vba-project/transfer-vba-user-form-and-macro/
---
## Wstęp

Witamy w Twoim ostatecznym przewodniku po ulepszaniu Twojego doświadczenia z Excelem za pomocą makr VBA i formularzy użytkownika! W tym samouczku pokażemy, jak przenieść projektanta makr VBA UserForm z jednego skoroszytu do drugiego za pomocą potężnej biblioteki Aspose.Cells for .NET. Niezależnie od tego, czy jesteś doświadczonym programistą, czy dopiero zaczynasz, ten przewodnik krok po kroku wyposaży Cię w wiedzę, aby programowo obsługiwać pliki Excela. Gotowy do zanurzenia się? Zaczynajmy!

## Wymagania wstępne
Zanim przejdziemy do kodowania, upewnijmy się, że masz wszystko, czego potrzebujesz:

1. Środowisko programistyczne C#: środowisko robocze do programowania w języku C#, w którym zdecydowanie zaleca się korzystanie z programu Visual Studio.
2.  Biblioteka Aspose.Cells dla .NET: Upewnij się, że integrujesz bibliotekę Aspose.Cells ze swoim projektem. Możesz łatwo[pobierz tutaj](https://releases.aspose.com/cells/net/).
3. Podstawowa wiedza na temat języka VBA i makr programu Excel: Znajomość języka VBA i sposobu działania makr programu Excel pogłębi Twoje zrozumienie tego samouczka.
4. Plik programu Excel z formularzem użytkownika: Utwórz lub uzyskaj skoroszyt programu Excel zawierający formularz użytkownika (najlepiej z włączonymi makrami, takimi jak`.xlsm` akta).

## Importowanie wymaganych pakietów
Aby wykorzystać funkcjonalności udostępniane przez Aspose.Cells, należy dodać następujące przestrzenie nazw na początku pliku C#:

```csharp
using System;
using Aspose.Cells;
using Aspose.Cells.Vba;
```

Te przestrzenie nazw dadzą ci dostęp do potężnych narzędzi osadzonych w bibliotece Aspose.Cells.

## Krok 1: Zdefiniuj katalogi źródłowe i wyjściowe
Najpierw ustal lokalizację swoich plików:

```csharp
// Zdefiniuj katalogi źródłowe i wyjściowe
string sourceDir = @"Your\Source\Directory\";
string outputDir = @"Your\Output\Directory\";
```

Zastąp ścieżki tymczasowe rzeczywistymi katalogami, w których przechowywane są Twoje pliki.

## Krok 2: Utwórz pusty skoroszyt docelowy
Następnie utwórz nowy skoroszyt, do którego skopiujesz formularz użytkownika i makra:

```csharp
// Utwórz pusty skoroszyt docelowy
Workbook target = new Workbook();
```

Spowoduje to utworzenie pustego skoroszytu, który będzie stanowił tło dla przyszłego transferu danych.

## Krok 3: Załaduj swój szablon skoroszytu
Załaduj skoroszyt zawierający formularz użytkownika i makra:

```csharp
// Załaduj plik Excel zawierający formularz użytkownika VBA-Macro Designer
Workbook templateFile = new Workbook(sourceDir + "sampleDesignerForm.xlsm");
```

Regulować`"sampleDesignerForm.xlsm"` do nazwy twojego rzeczywistego pliku.

## Krok 4: Kopiowanie arkuszy do skoroszytu docelowego
Teraz skopiujmy arkusze kalkulacyjne z szablonu do skoroszytu docelowego:

```csharp
// Skopiuj wszystkie arkusze szablonów do skoroszytu docelowego
foreach (Worksheet ws in templateFile.Worksheets)
{
    if (ws.Type == SheetType.Worksheet)
    {
        Worksheet s = target.Worksheets.Add(ws.Name);
        s.Copy(ws);
        // Dodaj wiadomość w komórce A2 arkusza docelowego
        s.Cells["A2"].PutValue("VBA Macro and User Form copied from template to target.");
    }
}
```

Kod ten przechodzi przez każdy arkusz w szablonie i kopiuje go do skoroszytu docelowego, zapewniając płynne przeniesienie wszystkich danych.

## Krok 5: Kopiuj makra VBA z szablonu
Następnie skopiujemy makra VBA, w tym moduły UserForm Designer, do nowego skoroszytu:

```csharp
// Kopiuj formularz użytkownika VBA-Macro Designer z szablonu do celu
foreach (VbaModule vbaItem in templateFile.VbaProject.Modules)
{
    if (vbaItem.Name == "ThisWorkbook")
    {
        // Skopiuj kod modułu ThisWorkbook
        target.VbaProject.Modules["ThisWorkbook"].Codes = vbaItem.Codes;
    }
    else
    {
        // Kopiuj kod i dane innych modułów
        int vbaMod = target.VbaProject.Modules.Add(vbaItem.Type, vbaItem.Name);
        target.VbaProject.Modules[vbaMod].Codes = vbaItem.Codes;

        if (vbaItem.Type == VbaModuleType.Designer)
        {
            // Pobierz magazyn projektanta formularzy użytkownika
            byte[] designerStorage = templateFile.VbaProject.Modules.GetDesignerStorage(vbaItem.Name);
            // Dodaj magazyn projektanta do docelowego projektu Vba
            target.VbaProject.Modules.AddDesignerStorage(vbaItem.Name, designerStorage);
        }
    }
}
```

Kod ten zapewnia, że nie tylko kod, ale także projekt formularza użytkownika zostanie skopiowany, dzięki czemu zachowana zostanie funkcjonalność makr.

## Krok 6: Zapisz skoroszyt docelowy
Po zakończeniu kopiowania zapisz nowy skoroszyt:

```csharp
// Zapisz skoroszyt docelowy
target.Save(outputDir + "outputDesignerForm.xlsm", SaveFormat.Xlsm);
```

Zmień nazwę pliku wyjściowego w razie potrzeby. Ten krok tworzy Twój dostosowany skoroszyt wypełniony makrami i formularzami użytkownika.

## Krok 7: Potwierdź powodzenie
Na koniec wyświetl na konsoli komunikat o powodzeniu operacji:

```csharp
Console.WriteLine("CopyVBAMacroUserFormDesignerStorageToWorkbook executed successfully.\r\n");
```

Ta prosta linijka daje Ci pewność, że cały proces przebiegł bez zakłóceń — jest to potwierdzenie Twojej ciężkiej pracy!

## Wniosek
Gratulacje! Udało Ci się nauczyć, jak kopiować makro VBA User Form Designer z jednego skoroszytu do drugiego, używając Aspose.Cells dla .NET. Choć na początku może się to wydawać przytłaczające, praktyka sprawi, że opanujesz manipulacje skoroszytami. Pamiętaj, że kodowanie polega na eksperymentowaniu, więc nie wahaj się odkrywać różnych funkcjonalności w plikach Excela. Jeśli masz jakieś pytania lub potrzebujesz pomocy, fora i dokumentacja Aspose to doskonałe źródła wsparcia.

## Najczęściej zadawane pytania

### Jakie wersje programu Excel obsługuje Aspose.Cells?
Aspose.Cells obsługuje różne formaty plików Excel, w tym XLSX, XLSM, CSV i inne.

### Czy mogę używać Aspose.Cells za darmo?
 Tak! Możesz zacząć od bezpłatnego okresu próbnego, aby ocenić bibliotekę:[Bezpłatna wersja próbna](https://releases.aspose.com/).

### Czy potrzebuję programu Visual Studio, aby uruchomić ten kod?
Chociaż zaleca się korzystanie z programu Visual Studio ze względu na jego przyjazne użytkownikowi funkcje, wystarczy każde środowisko IDE języka C# obsługujące programowanie w środowisku .NET.

### Gdzie mogę znaleźć więcej przykładów i dokumentacji?
 Możesz zbadać[Dokumentacja Aspose.Cells](https://reference.aspose.com/cells/net/) aby zobaczyć więcej przykładów i szczegółowych wyjaśnień.

### Jak rozwiązywać problemy podczas korzystania z Aspose.Cells?
 Powinieneś odwiedzić[Forum wsparcia Aspose](https://forum.aspose.com/c/cells/9) Aby uzyskać pomoc od społeczności i personelu pomocniczego Aspose.