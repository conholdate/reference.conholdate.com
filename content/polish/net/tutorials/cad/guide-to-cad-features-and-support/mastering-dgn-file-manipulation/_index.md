---
title: Opanowanie manipulacji plikami DGN za pomocą Aspose.CAD w .NET
linktitle: Opanowanie manipulacji plikami DGN
second_title: Aspose.CAD .NET — format pliku CAD i BIM
description: Dowiedz się, jak ładować pliki DGN, przeglądać ich elementy, zarządzać obiektami 2D i 3D oraz eksportować je jako obrazy rastrowe — wykorzystując przy tym zaawansowane funkcje biblioteki Aspose.CAD.
type: docs
weight: 18
url: /pl/net/tutorials/cad/guide-to-cad-features-and-support/mastering-dgn-file-manipulation/
---
## Wstęp

Czy jesteś programistą .NET, który chce zintegrować pliki DGN ze swoimi aplikacjami? Aspose.CAD dla .NET oferuje potężną bibliotekę zaprojektowaną specjalnie do pracy z formatami plików DGN. W tym samouczku zbadamy, jak wydajnie obsługiwać pliki DGN, w tym obsługiwane elementy, i jak nimi manipulować w swoich projektach .NET.

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące ustawienia:

- Podstawowa znajomość programowania .NET: Znajomość języka C# lub VB.NET będzie dodatkowym atutem.
- Visual Studio: zainstalowany na Twoim komputerze w celu realizacji projektu.
-  Biblioteka Aspose.CAD dla .NET: Pobierz ją ze strony[Aspose.CAD](https://releases.aspose.com/cad/net/).

## Krok 1: Importuj niezbędne przestrzenie nazw

Aby w pełni wykorzystać funkcjonalności Aspose.CAD, zacznij od zaimportowania wymaganych przestrzeni nazw do swojego projektu.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using Aspose.CAD;
using Aspose.CAD.FileFormats.Dgn;
using Aspose.CAD.FileFormats.Dgn.DgnElements;
```

## Krok 2: Załaduj plik DGN

 Zacznij od załadowania istniejącego pliku DGN do swojej aplikacji. Można to zrobić poprzez utworzenie instancji`DgnImage`.

```csharp
string myDir = "Your Document Directory";
string sourceFilePath = myDir + "Nikon_D90_Camera.dgn";

using (DgnImage dgnImage = (DgnImage)Image.Load(sourceFilePath))
{
    // Kontynuuj tutaj swoją logikę
}
```

## Krok 3: Iteruj po elementach DGN

Po załadowaniu pliku DGN możesz iterować jego elementy. Aspose.CAD udostępnia różnorodne typy elementów DGN do manipulacji.

```csharp
foreach (DgnDrawingElementBase element in dgnImage.Elements)
{
    // Przetwórz każdy element
}
```

## Krok 4: Obsługa obiektów 2D i 3D

Można rozróżnić elementy DGN 2D i 3D. Poniżej przedstawiono sposób ich wydajnego obsługiwania:

### Obsługa obiektów 2D

Można zarządzać wcześniej obsługiwanymi obiektami 2D za pomocą bloku switch-case.

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.Line:
    case DgnElementType.Ellipse:
    case DgnElementType.Curve:
        // Dodaj tutaj swoją logikę przetwarzania
        break;
}
```

### Obsługa obiektów 3D

Podobnie należy postępować z obiektami 3D w następujący sposób:

```csharp
switch (element.Metadata.Type)
{
    case DgnElementType.SolidHeader3D:
    case DgnElementType.Cone:
    case DgnElementType.CellHeader:
        // Dodaj tutaj swoją logikę przetwarzania
        break;
}
```

## Krok 5: Eksportuj plik DGN

Po manipulacji elementami DGN możesz chcieć wyeksportować plik jako obraz rastrowy. Można to łatwo zrobić za pomocą Aspose.CAD.

```csharp
string outputFilePath = myDir + "Exported_Image.png"; // Zdefiniuj ścieżkę wyjściową
dgnImage.Save(outputFilePath, new Aspose.CAD.ImageOptions.PngOptions());
Console.WriteLine($"\nThe DGN file exported successfully to raster image.\nFile saved at {outputFilePath}");
```

## Wniosek

W tym samouczku nauczyliśmy się, jak używać Aspose.CAD dla .NET, aby skutecznie zarządzać plikami DGN. Postępując zgodnie z opisanymi krokami, możesz bez wysiłku obsługiwać zarówno elementy 2D, jak i 3D DGN i eksportować je jako obrazy rastrowe. Ta potężna biblioteka umożliwia bezproblemową integrację przetwarzania DGN z aplikacjami .NET, zwiększając możliwości projektu.

## Najczęściej zadawane pytania

### Gdzie mogę znaleźć dokumentację Aspose.CAD dla .NET?

 Pełna dokumentacja jest dostępna[Tutaj](https://reference.aspose.com/cad/net/).

### Jak pobrać Aspose.CAD dla platformy .NET?

 Możesz pobrać najnowszą wersję biblioteki[Tutaj](https://releases.aspose.com/cad/net/).

### Czy jest dostępna bezpłatna wersja próbna Aspose.CAD dla .NET?

 Tak, dostępna jest bezpłatna wersja próbna[Tutaj](https://releases.aspose.com/).

### W jaki sposób mogę uzyskać tymczasową licencję na Aspose.CAD dla platformy .NET?

 Możesz poprosić o licencje tymczasowe[Tutaj](https://purchase.conholdate.com/temporary-license/).

### Potrzebujesz pomocy lub masz pytania?

Aby uzyskać pomoc lub zadać pytania, odwiedź społeczność Aspose.CAD[forum wsparcia](https://forum.aspose.com/c/cad/19).