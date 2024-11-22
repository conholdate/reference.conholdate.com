---
title: Zapisywanie dokumentów OneNote w formacie PDF przy użyciu Aspose.Note dla platformy .NET
linktitle: Zapisywanie dokumentów OneNote w formacie PDF
second_title: Aspose.Note .NET API
description: Dowiedz się, jak skutecznie zapisywać dokumenty Microsoft OneNote jako pliki PDF przy użyciu Aspose.Note dla .NET. Ten przewodnik przeprowadzi Cię przez niezbędne wymagania wstępne i oferuje pomocne FAQ.
type: docs
weight: 26
url: /pl/net/tutorials/note/one-note-document-manipulation/saving-one-note-document-pdf/
---
## Wstęp

W tym samouczku pokażemy, jak zapisywać dokumenty w formacie PDF za pomocą Aspose.Note dla .NET. Aspose.Note to potężna biblioteka, która umożliwia programistom pracę z plikami Microsoft OneNote programowo. Omówimy wymagania wstępne, zaimportujemy przestrzenie nazw i dostarczymy przewodniki krok po kroku dotyczące zapisywania dokumentów w formacie PDF w różnych układach stron.

## Wymagania wstępne
1. Visual Studio: Sprawdź, czy jest zainstalowany.
2. Aspose.Note dla .NET: Pobierz i zainstaluj bibliotekę.
3. Znajomość języka C#: Wymagana jest podstawowa znajomość języka.

## Importowanie niezbędnych przestrzeni nazw
Zanim przejdziesz dalej, zaimportuj do kodu następujące przestrzenie nazw:

```csharp
using System;
using System.IO;
using Aspose.Note.Saving;
```

## Krok 1: Zapisz do pliku PDF z ustawieniami strony Letter
```csharp
public static void SaveToPdfUsingLetterPageSettings()
{
    string dataDir = "Your Document Directory"; // Zaktualizuj tę ścieżkę
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingLetterPageSettings.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.Letter });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Ładuje dokument programu OneNote i zapisuje go w formacie PDF, używając ustawień rozmiaru strony Letter.

## Krok 2: Zapisz do pliku PDF z ustawieniami strony A4 (bez limitu wysokości)
```csharp
public static void SaveToPdfUsingA4PageSettingsWithoutHeightLimit()
{
    string dataDir = "Your Document Directory"; // Zaktualizuj tę ścieżkę
    Document oneFile = new Document(dataDir + "OneNote.one");
    var dst = Path.Combine(dataDir, "SaveToPdfUsingA4PageSettingsWithoutHeightLimit.pdf");
    
    oneFile.Save(dst, new PdfSaveOptions() { PageSettings = PageSettings.A4NoHeightLimit });
    Console.WriteLine("\nOneNote document saved successfully.\nFile saved at " + dst);
}
```
Podobnie jak w kroku 1, ale wykorzystuje ustawienia strony A4 bez ograniczeń wysokości.

## Wniosek
Samouczek skutecznie pokazuje, jak konwertować pliki OneNote do formatu PDF za pomocą Aspose.Note. Dzięki wykorzystaniu różnych ustawień strony programiści zyskują elastyczność w zarządzaniu dokumentami.

## Najczęściej zadawane pytania
### Czy Aspose.Note obsługuje złożone pliki OneNote?
Tak, skutecznie obsługuje różne funkcje złożonych plików OneNote.

### Czy Aspose.Note nadaje się do projektów komercyjnych?
Tak, po zakupieniu licencji można używać go w celach komercyjnych.

### Czy Aspose.Note oferuje bezpłatny okres próbny?
Tak, dostępna jest bezpłatna wersja próbna.

### Gdzie mogę znaleźć dokumentację dla Aspose.Note?
Szczegółowa dokumentacja jest dostępna na stronie referencyjnej Aspose.

### Potrzebujesz dalszej pomocy?
Jeśli masz pytania lub potrzebujesz pomocy, odwiedź forum Aspose.Note.
