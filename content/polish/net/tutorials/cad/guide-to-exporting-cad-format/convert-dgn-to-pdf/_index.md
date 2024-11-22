---
title: Konwersja DGN do PDF w Aspose.CAD dla .NET
linktitle: Konwersja DGN do PDF w Aspose.CAD dla .NET
second_title: Aspose.CAD .NET — format pliku CAD i BIM
description: Dowiedz się, jak bez wysiłku konwertować pliki DGN do PDF, korzystając z potężnej biblioteki Aspose.CAD dla .NET. Ten przewodnik krok po kroku jest przeznaczony dla programistów na każdym poziomie.
type: docs
weight: 12
url: /pl/net/tutorials/cad/guide-to-exporting-cad-format/convert-dgn-to-pdf/
---
## Wstęp

Poruszanie się po świecie plików CAD może być trudne, ale dzięki Aspose.CAD dla .NET programiści mogą łatwo manipulować i konwertować różne formaty CAD. Jedną z powszechnych potrzeb jest konwersja plików DGN do PDF, którą omówimy krok po kroku w tym samouczku.

## Wymagania wstępne

Aby móc kontynuować, upewnij się, że masz następujące informacje:

- Podstawowa znajomość języka C# i środowiska .NET.
-  Biblioteka Aspose.CAD dla .NET została zainstalowana. Możesz ją pobrać[Tutaj](https://releases.aspose.com/cad/net/).
- Przykładowy plik DGN (np. Nikon_D90_Camera.dgn). 

## Krok 1: Importuj wymagane przestrzenie nazw

Zacznij od zaimportowania odpowiednich przestrzeni nazw do swojego projektu C#:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
```

## Krok 2: Załaduj plik DGN

Określ katalog dla pliku DGN i załaduj go, korzystając z następującego kodu:

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage cadImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Dalsze przetwarzanie nastąpi tutaj...
}
```

## Krok 3: Skonfiguruj opcje rasteryzacji

Następnie skonfiguruj opcje rasteryzacji, aby zdefiniować sposób renderowania pliku DGN w pliku PDF:

```csharp
CadRasterizationOptions rasterizationOptions = new CadRasterizationOptions
{
    PageWidth = 600, // Dostosuj szerokość według potrzeb
    PageHeight = 300, // Dostosuj wysokość według potrzeb
    NoScaling = true,
    AutomaticLayoutsScaling = false
};
```

## Krok 4: Utwórz opcje PDF

Zdefiniuj opcje PDF, integrując wcześniej skonfigurowane ustawienia rasteryzacji:

```csharp
PdfOptions pdfOptions = new PdfOptions
{
    VectorRasterizationOptions = rasterizationOptions
};
```

## Krok 5: Zapisz DGN jako PDF

Na koniec zapisz plik DGN jako PDF, korzystając z skonfigurowanych opcji:

```csharp
cadImage.Save(myDir + "ExportDGNToPdf_out.pdf", pdfOptions);
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować plik DGN na PDF przy użyciu Aspose.CAD dla .NET. Ten prosty samouczek poprowadził Cię przez ładowanie pliku DGN, ustawianie opcji rasteryzacji i zapisywanie wyników jako PDF.

## Najczęściej zadawane pytania

### Czy muszę mieć wcześniejszą wiedzę z zakresu CAD, aby używać Aspose.CAD?  
Oczywiście! Aspose.CAD został zaprojektowany, aby uprościć złożone zadania CAD, czyniąc je dostępnymi dla wszystkich programistów, niezależnie od ich wiedzy CAD.

### Gdzie mogę znaleźć więcej materiałów i dokumentacji dla Aspose.CAD?  
 Możesz zapoznać się z kompleksowymi przewodnikami i przykładami w[Dokumentacja Aspose.CAD](https://reference.aspose.com/cad/net/).

### Czy jest dostępna bezpłatna wersja próbna Aspose.CAD?  
 Tak, można uzyskać bezpłatną wersję próbną[Tutaj](https://releases.aspose.com/).

### Jak mogę uzyskać tymczasową licencję na Aspose.CAD?  
 Możesz poprosić o licencje tymczasowe[Tutaj](https://purchase.conholdate.com/temporary-license/).

### Potrzebujesz pomocy lub masz pytania?  
Dołącz do rozmowy w[Forum Aspose.CAD](https://forum.aspose.com/c/cad/19) w celu uzyskania wsparcia społeczności lub w celu uzyskania odpowiedzi na pytania.