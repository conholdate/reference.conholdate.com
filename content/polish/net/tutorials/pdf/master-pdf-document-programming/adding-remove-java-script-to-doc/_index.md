---
title: Dodawanie Usuń JavaScript Do Dokumentu PDF
linktitle: Dodawanie Usuń JavaScript Do Dokumentu PDF
second_title: Aspose.PDF dla .NET API Reference
description: Ten kompleksowy przewodnik pokazuje, jak dodawać niestandardowe zachowania, dynamicznie wykonywać obliczenia lub walidacje i integrować się z innymi aplikacjami.
type: docs
weight: 30
url: /pl/net/tutorials/pdf/master-pdf-document-programming/adding-remove-java-script-to-doc/
---
## Wstęp

W tym kompleksowym przewodniku zagłębimy się w świat Aspose.PDF dla .NET i uwolnimy jego pełny potencjał, aby dodać niestandardową funkcjonalność JavaScript do dokumentów PDF. Ta potężna funkcja pozwala na włączenie dynamicznych elementów, ulepszenie doświadczenia użytkownika i usprawnienie przepływów pracy.

## Wymagania wstępne

Aby śledzić, będziesz potrzebować:

1. Aspose.PDF dla .NET zainstalowany w Twoim projekcie (do pobrania z[Strona pobierania Aspose.PDF dla .NET](https://releases.aspose.com/pdf/net/))
2. Ważna licencja na korzystanie z biblioteki
3. AC# IDE lub edytor tekstu

## Importuj pakiety

Na początek zaimportuj niezbędne przestrzenie nazw do swojego projektu:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
using System.Collections;
```

## Krok 1: Zainicjuj nowy dokument PDF

Utwórz nowy dokument PDF i dodaj go do swojego płótna:

```csharp
Document doc = new Document();
doc.Pages.Add();
```

W tym miejscu zaczniesz tworzyć dokument PDF oparty na języku JavaScript.

## Krok 2: Dodaj JavaScript do pliku PDF

 Wstaw funkcje JavaScript do swojego dokumentu za pomocą`doc.JavaScript` kolekcja. Oto przykład:

```csharp
doc.JavaScript["func1"] = "function func1() { console.log('Hello'); }";
doc.JavaScript["func2"] = "function func2() { alert('This is a test'); }";
```

## Krok 3: Zapisz plik PDF za pomocą JavaScript

Zapisz zaktualizowany dokument na dysku:

```csharp
doc.Save(dataDir + "AddJavascript.pdf");
```

Teraz możesz uzyskać dostęp do kodu JavaScript i modyfikować go w istniejącym pliku PDF.

## Krok 4: Załaduj i wyświetl JavaScript w istniejącym pliku PDF

 Załaduj plik PDF zawierający JavaScript i uzyskaj dostęp do jego kluczy za pomocą`Keys` nieruchomość:

```csharp
Document doc1 = new Document(dataDir + "AddJavascript.pdf");
IList keys = (System.Collections.IList)doc1.JavaScript.Keys;
```

## Krok 5: Wyświetl funkcje JavaScript

Przejdź przez klucze JavaScript i wydrukuj odpowiadający im kod na konsoli:

```csharp
Console.WriteLine("=============================== ");
foreach (string key in keys)
{
    Console.WriteLine(key + " ==> " + doc1.JavaScript[key]);
}
```

Pokazuje, jak można sprawdzić, które funkcje JavaScript są aktualnie obecne.

## Krok 6: Usuń JavaScript z pliku PDF

Znajdź żądaną funkcję JavaScript według jej nazwy i usuń ją:

```csharp
doc1.JavaScript.Remove("func1");
Console.WriteLine("Key 'func1' removed ");
```

Sprawdź, czy funkcja została pomyślnie usunięta poprzez ponowne wydrukowanie pozostałych funkcji.

## Wniosek

W tym kompleksowym przewodniku odkryłeś, jak odblokować moc Aspose.PDF dla dostosowywalnej funkcjonalności JavaScript .NET. Dzięki tej funkcji możesz tworzyć dynamiczne pliki PDF, ulepszać doświadczenia użytkowników i usprawniać przepływy pracy. Opanowując te kroki i dalej eksplorując możliwości biblioteki, będziesz na dobrej drodze do odblokowania nowych możliwości w swoich aplikacjach.

## Najczęściej zadawane pytania

### Czy mogę dodać wiele funkcji JavaScript do jednego pliku PDF?
 Tak! Możesz dodać tyle funkcji JavaScript, ile potrzebujesz, używając`doc.JavaScript` kolekcja.

### Co się stanie, jeśli spróbuję usunąć nieistniejącą funkcję JavaScript?
 Jeżeli funkcja nie istnieje,`Remove`Metoda nie zgłosi błędu, ale też niczego nie usunie. Aby obsłużyć nieistniejące funkcje, możesz dodać dodatkową obsługę błędów lub zmodyfikować kod, aby je zignorować.

### Czy można uruchomić JavaScript od razu po otwarciu pliku PDF?
Tak! Możesz skonfigurować JavaScript tak, aby działał na określonych wyzwalaczach, takich jak otwieranie dokumentu lub klikanie przycisku.

### Czy mogę edytować JavaScript po dodaniu go do pliku PDF?
Tak, możesz załadować istniejący plik PDF, uzyskać dostęp do jego kodu JavaScript, zmodyfikować kod i ponownie zapisać dokument.

### Czy usunięcie JavaScriptu ma wpływ na pozostałą zawartość pliku PDF?
Nie, usunięcie JavaScript wpływa tylko na skrypt. Zawartość pliku PDF pozostaje niezmieniona.