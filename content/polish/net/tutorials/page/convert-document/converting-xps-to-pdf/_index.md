---
title: Konwersja XPS do PDF za pomocą Aspose.Page dla .NET
linktitle: Konwersja XPS do PDF
second_title: Aspose.Page .NET API
description: Odkryj, jak bezproblemowo konwertować dokumenty XPS (XML Paper Specification) do formatu PDF (Portable Document Format) przy użyciu zaawansowanej biblioteki Aspose.Page for .NET.
type: docs
weight: 11
url: /pl/net/tutorials/page/convert-document/converting-xps-to-pdf/
---
## Wstęp

tym samouczku pokażemy, jak konwertować dokumenty XPS (XML Paper Specification) na PDF (Portable Document Format) przy użyciu wszechstronnej biblioteki Aspose.Page for .NET. Ta potężna biblioteka upraszcza konwersję dokumentów i oferuje różne opcje dostosowywania, co czyni ją doskonałym wyborem dla programistów.

## Wymagania wstępne

Zanim zaczniemy, upewnij się, że masz następujące rzeczy:

-  Biblioteka Aspose.Page dla platformy .NET: Pobierz i zainstaluj bibliotekę Aspose.Page dla platformy .NET z[Dokumentacja Aspose.Page](https://reference.aspose.com/page/net/).
  
- Środowisko programistyczne: skonfiguruj środowisko programistyczne .NET za pomocą programu Visual Studio lub innego zgodnego środowiska IDE.

- Dokument XPS: Przygotuj plik XPS, który chcesz przekonwertować, i zapisz go w wyznaczonym katalogu.

## Krok 1: Importuj wymagane przestrzenie nazw

Zacznij od zaimportowania niezbędnej przestrzeni nazw, aby uzyskać dostęp do funkcjonalności Aspose.Page:

```csharp
using Aspose.Page.XPS;
```

## Krok 2: Zainicjuj katalog dokumentów

Zdefiniuj ścieżkę katalogu, w którym przechowywane są Twoje dokumenty:

```csharp
string dataDir = "Your Document Directory";
```

 Pamiętaj o wymianie`"Your Document Directory"` z rzeczywistą ścieżką do katalogu zawierającego dokument XPS.

### Krok 3: Otwórz strumienie PDF i XPS

Następnie zainicjuj strumienie zarówno dla pliku wejściowego XPS, jak i wyjściowego PDF:

```csharp
using (System.IO.Stream pdfStream = System.IO.File.Open(dataDir + "XPStoPDF_out.pdf", System.IO.FileMode.OpenOrCreate, System.IO.FileAccess.Write))
using (System.IO.Stream xpsStream = System.IO.File.Open(dataDir + "input.xps", System.IO.FileMode.Open))
```

Upewnij się, że ścieżka do plików jest prawidłowa.

### Krok 4: Załaduj dokument XPS

Teraz załaduj dokument XPS korzystając z biblioteki Aspose.Page:

```csharp
XpsDocument document = new XpsDocument(xpsStream, new XpsLoadOptions());
```

### Krok 5: Skonfiguruj opcje zapisywania pliku PDF

Skonfiguruj opcje zapisu pliku PDF, w tym jakość obrazu i parametry kompresji:

```csharp
PdfSaveOptions options = new PdfSaveOptions()
{
    JpegQualityLevel = 100, // Ustaw poziom jakości JPEG
    ImageCompression = PdfImageCompression.Jpeg, // Użyj kompresji JPEG dla obrazów
    TextCompression = PdfTextCompression.Flate, // Zastosuj kompresję Flate dla tekstu
    PageNumbers = new int[] { 1, 2, 6 } // Podaj numery stron, które chcesz uwzględnić
};
```

Możesz swobodnie dostosować te parametry do swoich potrzeb.

### Krok 6: Utwórz urządzenie renderujące PDF

Utwórz urządzenie renderujące dla formatu PDF:

```csharp
PdfDevice device = new PdfDevice(pdfStream);
```

### Krok 7: Zapisz dokument jako PDF

Na koniec zapisz dokument XPS w formacie PDF, używając określonego urządzenia i opcji:

```csharp
document.Save(device, options);
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować dokument XPS na PDF przy użyciu Aspose.Page dla .NET. Ta biblioteka nie tylko upraszcza konwersję dokumentów, ale także oferuje rozbudowane możliwości obsługi różnych formatów.

## Najczęściej zadawane pytania

### Czy mogę przekonwertować wiele plików XPS do jednego pliku PDF?

Oczywiście! Możesz iterować przez wiele plików XPS i scalać je w jeden dokument PDF, wykonując te same kroki konwersji.

### Jakie inne formaty wyjściowe obsługuje Aspose.Page dla .NET?

Oprócz formatu PDF Aspose.Page dla platformy .NET obsługuje szereg formatów, w tym TIFF, JPEG i PNG.

### Jak mogę dostosować wygląd przekonwertowanego pliku PDF?

 Możesz dostosować parametry w`PdfSaveOptions` obiektu, takiego jak jakość JPEG i ustawienia kompresji, aby uzyskać pożądany wygląd.

### Czy jest dostępna wersja próbna Aspose.Page dla .NET?

 Tak, możesz wypróbować Aspose.Page dla .NET dzięki bezpłatnej wersji próbnej[Tutaj](https://releases.aspose.com/).

### Gdzie mogę znaleźć wsparcie społeczności dla Aspose.Page dla .NET?

Aby wziąć udział w dyskusjach i uzyskać wsparcie społeczności, odwiedź stronę[Forum Aspose.Page](https://forum.aspose.com/c/page/39).