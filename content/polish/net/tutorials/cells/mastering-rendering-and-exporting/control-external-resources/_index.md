---
title: Kontroluj zasoby zewnętrzne za pomocą Aspose.Cells dla .NET
linktitle: Kontroluj zasoby zewnętrzne za pomocą Aspose.Cells dla .NET
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Odblokuj pełny potencjał konwersji Excel do PDF dzięki Aspose.Cells dla .NET. W tym kompleksowym przewodniku dowiesz się, jak zarządzać zasobami zewnętrznymi, takimi jak obrazy, zapewniając, że Twoje pliki PDF odzwierciedlają dokładne wymagania dotyczące formatowania.
type: docs
weight: 12
url: /pl/net/tutorials/cells/mastering-rendering-and-exporting/control-external-resources/
---
## Wstęp

dzisiejszym cyfrowym krajobrazie konwersja arkuszy kalkulacyjnych Excela na dokumenty PDF jest powszechnym i niezbędnym zadaniem. Niezależnie od tego, czy przygotowujesz raporty, dane finansowe czy materiały prezentacyjne, upewnienie się, że Twoje pliki PDF odzwierciedlają zamierzony format, jest kluczowe. Aspose.Cells dla .NET zapewnia potężną bibliotekę, która pozwala kontrolować ten proces konwersji szczegółowo, szczególnie w przypadku zasobów zewnętrznych, takich jak obrazy. W tym przewodniku przyjrzymy się, jak skutecznie zarządzać zasobami zewnętrznymi podczas procesu konwersji Excela na PDF przy użyciu Aspose.Cells. Zanurzmy się!

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz przygotowane następujące rzeczy:

1. Visual Studio lub dowolne środowisko IDE zgodne z platformą .NET: To będzie Twoje środowisko programistyczne.
2.  Aspose.Cells dla .NET: Jeśli jeszcze nie zainstalowałeś, odwiedź stronę[Pobieranie Aspose](https://releases.aspose.com/cells/net/) aby pobrać najnowszą wersję.
3. Podstawowa wiedza o C#: Znajomość C# będzie korzystna. Jeśli potrzebujesz wyjaśnień odnośnie jakichkolwiek pojęć, możesz je sprawdzić.
4. Przykładowy plik Excela: Przygotuj plik Excela, taki jak „samplePdfSaveOptions_StreamProvider.xlsx”, zawierający zasoby zewnętrzne, które chcesz przekonwertować.
5. Plik obrazu do testowania: Podczas konwersji użyj pliku obrazu, takiego jak „newPdfSaveOptions_StreamProvider.png”, jako zasobu zewnętrznego.

## Importuj niezbędne pakiety

Na początek musisz zaimportować wymagane przestrzenie nazw z biblioteki Aspose.Cells. Dodaj następujące dyrektywy using na górze pliku C#:

```csharp
using System.IO;
using System.Drawing;
using System.Drawing.Imaging;
using Aspose.Cells;
using Aspose.Cells.Drawing;
using Aspose.Cells.Rendering;
using System;
```

Te przestrzenie nazw zapewniają podstawowe klasy i metody dla Twoich zadań.

## Krok 1: Utwórz klasę dostawcy strumienia

 Najpierw utwórz klasę dostawcy strumienia, która implementuje`IStreamProvider` interfejs. Ta klasa umożliwi Ci kontrolowanie sposobu ładowania zasobów zewnętrznych.

```csharp
class MyStreamProvider : IStreamProvider
{
    public void CloseStream(StreamProviderOptions options)
    {
        Debug.WriteLine("-----Close Stream-----");
    }

    public void InitStream(StreamProviderOptions options)
    {
        string sourceDir = "Your Document Directory";
        Debug.WriteLine("-----Init Stream-----");
        
        // Załaduj obraz do strumienia pamięci
        byte[] bts = File.ReadAllBytes(Path.Combine(sourceDir, "newPdfSaveOptions_StreamProvider.png"));
        MemoryStream ms = new MemoryStream(bts);
        options.Stream = ms;
    }
}
```

- CloseStream: Ta metoda jest wywoływana po zamknięciu strumienia; obecnie rejestrowany jest komunikat debugowania.
- InitStream: Ta metoda odczytuje zewnętrzny plik obrazu jako tablicę bajtów, konwertuje go na strumień pamięci i przypisuje do`options.Stream` nieruchomość.

## Krok 2: Skonfiguruj katalogi źródłowe i wyjściowe

Następnie zdefiniuj katalogi dla pliku Excel i wyjściowego pliku PDF.

```csharp
// Katalog źródłowy
string sourceDir = "Your Document Directory";
// Katalog wyjściowy
string outputDir = "Your Document Directory";
```

 Zastępować`"Your Document Directory"` z rzeczywistą ścieżką w systemie, gdzie znajdują się Twoje pliki.

## Krok 3: Załaduj plik Excel

Teraz załaduj plik Excela, z którego chcesz utworzyć plik PDF.

```csharp
// Załaduj plik źródłowy Excel zawierający obrazy zewnętrzne
Workbook wb = new Workbook(sourceDir, "samplePdfSaveOptions_StreamProvider.xlsx");
```

 Ten`Workbook` Klasa Aspose.Cells reprezentuje plik Excel, który może zawierać różne zasoby zewnętrzne, takie jak obrazy.

## Krok 4: Ustaw opcje zapisywania pliku PDF

Przed zapisaniem skoroszytu w formacie PDF określ żądane opcje zapisu.

```csharp
// Określ opcje zapisywania pliku PDF - Dostawca strumienia
PdfSaveOptions opts = new PdfSaveOptions
{
    OnePagePerSheet = true // Zapisz każdy arkusz na nowej stronie
};
```

 Tworzy to instancję`PdfSaveOptions` , co pozwala na dostosowanie formatu PDF.`OnePagePerSheet` Opcja ta zapewnia, że każdy arkusz programu Excel pojawi się na osobnej stronie w ostatecznym pliku PDF.

## Krok 5: Przypisz swojego dostawcę strumienia

 Połącz swoje`Workbook` instancja z`MyStreamProvider` klasa, którą utworzyłeś wcześniej.

```csharp
wb.Settings.StreamProvider = new MyStreamProvider();
```

Ten wiersz zapewnia, że za każdym razem, gdy podczas konwersji napotkane zostaną zasoby zewnętrzne, Twój dostawca usług będzie nimi odpowiednio zarządzał.

## Krok 6: Zapisz skoroszyt jako plik PDF

Teraz zapisz skoroszyt programu Excel w formacie PDF.

```csharp
// Zapisz skoroszyt w formacie PDF
wb.Save(outputDir + "outputPdfSaveOptions_StreamProvider.pdf", opts);
```

 Dzwoniąc do`Save` na obiekcie skoroszytu i przekazując katalog wyjściowy wraz z opcjami PDF, można przekonwertować plik Excela do poprawnie sformatowanego pliku PDF.

## Krok 7: Potwierdź pomyślne wykonanie

Na koniec warto potwierdzić, że proces zakończył się pomyślnie.

```csharp
Console.WriteLine("ControlLoadingOfExternalResourcesInExcelToPDF executed successfully.\r\n");
```

Ta wiadomość poinformuje Cię o stanie Twojej operacji i zapewni Ci przydatne informacje zwrotne.

## Wniosek

Opanowałeś już proces kontrolowania zasobów zewnętrznych podczas konwersji Excela do PDF za pomocą Aspose.Cells! Wykonując te kroki, możesz mieć pewność, że Twoje dokumenty dokładnie zawierają obrazy i inne elementy zewnętrzne, co za każdym razem skutkuje dopracowanym produktem końcowym.

## Najczęściej zadawane pytania

### Czym jest Aspose.Cells?
Aspose.Cells to zaawansowana biblioteka dla programistów .NET umożliwiająca tworzenie, przetwarzanie, konwersję i renderowanie plików Excel w różnych formatach.

### Jak pobrać Aspose.Cells?
 Najnowszą wersję można pobrać ze strony[Link do pobrania](https://releases.aspose.com/cells/net/).

### Czy mogę wypróbować Aspose.Cells za darmo?
 Tak! Możesz uzyskać dostęp do bezpłatnej wersji próbnej, odwiedzając stronę[Bezpłatna strona próbna](https://releases.aspose.com/).

### Gdzie mogę znaleźć pomoc dotyczącą Aspose.Cells?
 W przypadku pytań dotyczących pomocy technicznej odwiedź stronę[Forum wsparcia Aspose](https://forum.aspose.com/c/cells/9).

### Jak mogę uzyskać tymczasową licencję na Aspose.Cells?
 Możesz złożyć wniosek o tymczasową licencję[Tutaj](https://purchase.aspose.com/temporary-license/).
