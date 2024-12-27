---
title: Zmiana dostosowania czcionki MHT za pomocą języka C#
linktitle: Zmiana dostosowania czcionki MHT za pomocą języka C#
second_title: Aspose.Email .NET API przetwarzania poczty e-mail
description: Dowiedz się, jak zmieniać czcionki podczas konwersji MHT za pomocą Aspose.Email dla .NET. Postępuj zgodnie z tym przewodnikiem krok po kroku, aby ułatwić dostosowanie.
type: docs
weight: 11
url: /pl/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## Wstęp

W świecie komunikacji internetowej pliki MHT (MHTML) są przydatnym sposobem przechowywania i udostępniania treści internetowych, wraz z obrazami, linkami i stylami. Ale co się stanie, gdy będziesz musiał odświeżyć te pliki MHT, zmieniając czcionki? Dzięki Aspose.Email dla .NET to zadanie staje się dziecinnie proste. W tym samouczku przeprowadzimy Cię przez proces zmiany czcionek podczas konwersji MHT, krok po kroku. Niezależnie od tego, czy rozwijasz aplikację, która obsługuje formatowanie wiadomości e-mail, czy po prostu chcesz dostosować dokumenty do swojej firmy, ten przewodnik wyposaży Cię w potrzebną wiedzę.

## Wymagania wstępne

Zanim zagłębisz się w kod, powinieneś przygotować kilka niezbędnych rzeczy:

1. Visual Studio: Do pracy nad projektem w języku C# potrzebne będzie zintegrowane środowisko programistyczne (IDE).
2.  Aspose.Email dla biblioteki .NET: Upewnij się, że biblioteka jest zainstalowana. Możesz ją pobrać ze strony[połączyć](https://releases.aspose.com/email/net/).
3. .NET Framework: Twój projekt powinien być zgodny z platformą .NET Framework; zazwyczaj dobrze sprawdza się platforma .NET Core lub nowsze wersje.

Masz je ustawione? Super! Zaczynajmy.

## Importowanie pakietów

Najpierw upewnij się, że Twój projekt jest skonfigurowany do używania niezbędnych przestrzeni nazw. Będziesz chciał uwzględnić poniższe na górze swojego pliku C#:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

Pakiety te zapewnią Ci dostęp do funkcjonalności potrzebnych do pracy z plikami MHT i modyfikowania ich zawartości.

Przyjrzyjmy się teraz krokom związanym ze zmianą czcionek podczas konwersji MHT.

## Krok 1: Załaduj plik MHT

 Pierwszą rzeczą, którą musisz zrobić, jest załadowanie pliku MHT do`MailMessage` obiekt. Tutaj możesz uzyskać dostęp i manipulować jego zawartością.

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 Wyjaśnienie: Tutaj,`"input.mht"` jest ścieżką do pliku MHT.`MhtmlLoadOptions()`umożliwia skonfigurowanie sposobu ładowania pliku, np. w inny sposób obsługując załączniki lub powiązane zasoby.

## Krok 2: Iteruj przez alternatywne widoki

Pliki MHT często mają wiele alternatywnych widoków, zwłaszcza jeśli zawierają zawartość HTML. Musisz przejść przez te widoki, aby znaleźć ten, który chcesz zmodyfikować.

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 Wyjaśnienie: Sprawdzasz każdy`AlternateView` aby sprawdzić, czy jest to typ HTML. Jeśli tak, możesz uzyskać dostęp`LinkedResources`, w którym zazwyczaj przechowywane są wszystkie czcionki powiązane z kodem HTML.

## Krok 3: Zidentyfikuj i dostosuj czcionki

Teraz, gdy masz już dostęp do powiązanych zasobów, możesz zidentyfikować, które zasoby są czcionkami i dostosować je według potrzeb.

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // Zmień na żądaną czcionkę
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // Upewnij się, że jest poprawnie zakodowany
    }
}
```

 Wyjaśnienie: Ta pętla sprawdza, czy typ zawartości powiązanego zasobu jest czcionką TrueType. Jeśli pasuje, możesz zmienić nazwę czcionki na taką, jaką chcesz (np. „Arial” w tym przykładzie).`TransferEncoding`należy również ustawić tak, aby zapewnić prawidłowe kodowanie danych dotyczących czcionki podczas zapisywania dokumentu.

## Krok 4: Zapisz zaktualizowany plik MHT

Po dostosowaniu czcionek nadszedł czas na zapisanie zmodyfikowanego pliku MHT. Musisz upewnić się, że używasz prawidłowych opcji zapisu, aby zachować integralność pliku.

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 Wyjaśnienie: W tym wierszu kodu,`"output.mht"` jest nazwą pliku, w którym chcesz zapisać zaktualizowaną zawartość. Używanie`SaveOptions.DefaultMhtml` zapewnia, że nowy plik zachowa format MHT.

## Wniosek

Zmiana czcionek w plikach MHT może znacznie poprawić wygląd i styl Twoich dokumentów. Wykorzystując Aspose.Email dla .NET, możesz łatwo ładować pliki MHT, modyfikować ich zawartość i zapisywać zmiany, używając zaledwie kilku linijek kodu. Niezależnie od tego, czy pracujesz nad osobistym projektem, czy większą aplikacją, opanowanie tych umiejętności może poprawić sposób prezentacji informacji.

## Najczęściej zadawane pytania

### Co to jest format MHT?
MHT to format archiwum stron internetowych, który przechowuje dokumenty HTML, obrazy i inne zasoby w jednym pliku.

### Czy mogę zmienić inne aspekty plików MHT za pomocą Aspose?
Oczywiście! Aspose.Email pozwala modyfikować niemal każdy aspekt plików MHT, w tym załączniki, nagłówki i wiele innych.

### Czy Aspose.Email dla .NET jest darmowy?
 Aspose oferuje bezpłatną wersję próbną, ale pełna wersja wymaga licencji. Możesz uzyskać tymczasową licencję od[Tutaj](https://purchase.aspose.com/temporary-license/).

### Gdzie mogę znaleźć więcej dokumentacji na temat Aspose.Email?
 Pełną dokumentację i przykłady można znaleźć na stronie[Strona dokumentacji Aspose Email](https://reference.aspose.com/email/net/).

### Co zrobić, jeśli napotkam problemy podczas korzystania z Aspose?
 Jeśli napotkasz jakiekolwiek problemy, możesz skontaktować się z pomocą techniczną na stronie[Forum wsparcia Aspose](https://forum.aspose.com/c/email/12/).