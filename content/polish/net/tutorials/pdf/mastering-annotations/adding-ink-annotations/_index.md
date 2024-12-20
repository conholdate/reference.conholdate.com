---
title: Dodawanie adnotacji atramentowych za pomocą Aspose.PDF dla .NET
linktitle: Dodawanie adnotacji atramentowych za pomocą Aspose.PDF dla .NET
second_title: Aspose.PDF dla .NET API Reference
description: Dowiedz się, jak sprawić, by Twoje dokumenty PDF były bardziej interaktywne i angażujące, dodając adnotacje atramentowe za pomocą Aspose.PDF dla .NET. Ten kompleksowy przewodnik przeprowadzi Cię przez cały proces.
type: docs
weight: 20
url: /pl/net/tutorials/pdf/mastering-annotations/adding-ink-annotations/
---
## Wstęp

Witamy w ekscytującym świecie manipulacji PDF z Aspose.PDF dla .NET! Niezależnie od tego, czy ulepszasz dokumenty do użytku profesjonalnego, projektów osobistych czy czegoś pomiędzy, jesteś we właściwym miejscu. W tym przewodniku przyjrzymy się praktycznej funkcji Aspose.PDF: dodawaniu adnotacji atramentowych do plików PDF. Ta funkcjonalność doskonale nadaje się do włączania odręcznych notatek lub podpisów, dzięki czemu dokumenty stają się bardziej interaktywne i angażujące.

## Wymagania wstępne

Zanim przejdziemy do kodu, upewnijmy się, że wszystko jest skonfigurowane:

1. .NET Framework: Upewnij się, że .NET Framework jest zainstalowany na Twoim komputerze. Aspose.PDF działa bezproblemowo z różnymi wersjami, w tym .NET Core.
2.  Biblioteka Aspose.PDF: Pobierz i odnieś się do biblioteki Aspose.PDF dla .NET w swoim projekcie. Możesz pobrać najnowszą wersję z[link do pobrania](https://releases.aspose.com/pdf/net/).
3. Edytor kodu: Chociaż można używać dowolnego edytora kodu, zdecydowanie polecamy program Visual Studio ze względu na przyjazny interfejs użytkownika umożliwiający współpracę z aplikacjami .NET.
4. Podstawowa wiedza o języku C#: Znajomość języka C# pomoże Ci płynnie poruszać się po przykładach kodowania.
5. Konfiguracja środowiska programistycznego: upewnij się, że Twoje środowisko IDE jest skonfigurowane pod kątem projektów .NET i że poprawnie odwołałeś się do biblioteki Aspose.PDF.

Gdy już spełnisz te wymagania wstępne, będziesz gotowy, aby zacząć dodawać adnotacje atramentowe do plików PDF!

## Importowanie niezbędnych pakietów

Zanim zagłębimy się w kodowanie, zaimportujmy wymagane pakiety. Na górze pliku C# dodaj następujące polecenia using:

```csharp
using System.IO;
using Aspose.Pdf.Annotations;
using Aspose.Pdf;
using System;
using System.Collections.Generic;
```

Te polecenia zapewnią dostęp do wszystkich klas i metod niezbędnych do pracy z adnotacjami PDF.

Przedstawimy proces dodawania adnotacji odręcznej do dokumentu PDF w przejrzystych krokach.

## Krok 1: Skonfiguruj dokument i katalog

Najpierw należy utworzyć dokument i ścieżkę do zapisania pliku wyjściowego:

```csharp
string dataDir = "YOUR DATA DIRECTORY";
Document doc = new Document();
```

 Tutaj,`dataDir` wskazuje na katalog, w którym zostanie zapisany wynikowy plik PDF i utworzymy nowy`Document` obiekt do edycji.

## Krok 2: Dodaj stronę do dokumentu

Następnie dodaj stronę do nowo utworzonego dokumentu:

```csharp
Page pdfPage = doc.Pages.Add();
```

Każdy plik PDF wymaga co najmniej jednej strony, dlatego ten krok jest konieczny.

## Krok 3: Zdefiniuj prostokąt rysunkowy

Teraz zdefiniuj, w którym miejscu strony chcesz umieścić adnotację atramentową:

```csharp
System.Drawing.Rectangle drect = new System.Drawing.Rectangle
{
    Height = (int)pdfPage.Rect.Height,
    Width = (int)pdfPage.Rect.Width,
    X = 0,
    Y = 0
};
Aspose.Pdf.Rectangle arect = Aspose.Pdf.Rectangle.FromRect(drect);
```

 Ten kod tworzy`Rectangle` obiekt określający obszar na stronie, w którym chcesz umieścić adnotację tuszem, obejmujący całą stronę.

## Krok 4: Przygotuj punkty atramentowe

Następnie zdefiniuj punkty, które będą stanowić Twoją adnotację tuszem:

```csharp
IList<Point[]> inkList = new List<Point[]>();
Aspose.Pdf.Point[] arrpt = new Aspose.Pdf.Point[3];
inkList.Add(arrpt);
arrpt[0] = new Aspose.Pdf.Point(100, 800);
arrpt[1] = new Aspose.Pdf.Point(200, 800);
arrpt[2] = new Aspose.Pdf.Point(200, 700);
```

Ten blok tworzy listę tablic punktów, gdzie każda tablica reprezentuje zbiór punktów dla pociągnięcia tuszem. Tutaj definiujemy trzy punkty tworzące trójkąt, ale możesz swobodnie dostosować współrzędne, aby pasowały do Twojego projektu.

## Krok 5: Utwórz adnotację atramentową

Mając już zdefiniowane punkty, utwórz adnotację atramentową:

```csharp
InkAnnotation ia = new InkAnnotation(pdfPage, arect, inkList)
{
    Title = "Your Title",
    Color = Aspose.Pdf.Color.LightBlue,
    CapStyle = CapStyle.Rounded
};
```

 Utworzyliśmy instancję`InkAnnotation` obiekt, przekazując stronę, prostokąt i punkty atramentu. Dostosuj właściwości, takie jak`Title`, `Color` , I`CapStyle` aby spełnić Twoje potrzeby!

## Krok 6: Ustaw obramowanie i krycie

Aby wyróżnić swoją adnotację, nadaj jej styl:

```csharp
Border border = new Border(ia)
{
    Width = 25
};
ia.Border = border;
ia.Opacity = 0.5;
```

Ten kod dodaje obramowanie o określonej szerokości i ustawia krycie adnotacji, aby stała się półprzezroczysta.

## Krok 7: Dodaj adnotację do strony

Teraz dodaj swoją adnotację do strony PDF:

```csharp
pdfPage.Annotations.Add(ia);
```

Ten wiersz dodaje adnotację atramentową do zbioru adnotacji strony.

## Krok 8: Zapisz dokument

Na koniec zapisz zmodyfikowany dokument:

```csharp
dataDir = dataDir + "AddInkAnnotation_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nInk annotation added successfully.\nFile saved at " + dataDir);
```

 Tutaj modyfikujemy`dataDir` aby uwzględnić nazwę pliku wyjściowego i zapisać dokument. Wiadomość potwierdzająca powiadomi Cię, że wszystko poszło gładko.

## Wniosek

Gratulacje! Udało Ci się dodać adnotację atramentową do dokumentu PDF za pomocą Aspose.PDF dla .NET. Ta prosta, ale potężna funkcja może ulepszyć Twoje dokumenty i uczynić je interaktywnymi. Niezależnie od tego, czy dodajesz podpisy, notatki czy rysunki, adnotacje atramentowe zapewniają wyjątkowy sposób na wzbogacenie treści.

## Najczęściej zadawane pytania

### Czym jest Aspose.PDF?
Aspose.PDF to biblioteka umożliwiająca tworzenie, edytowanie i konwertowanie dokumentów PDF w aplikacjach .NET.

### Czy mogę używać Aspose.PDF bezpłatnie?
Tak! Aspose oferuje bezpłatną wersję próbną do oceny swoich produktów. Możesz ją pobrać[Tutaj](https://releases.aspose.com/).

### Czy można dodać wiele adnotacji atramentowych?
 Oczywiście! Możesz utworzyć wiele`InkAnnotation` obiekty i dodaj je do strony swojego dokumentu.

### Gdzie mogę znaleźć więcej przykładów?
 Sprawdź[dokumentacja](https://reference.aspose.com/pdf/net/) aby uzyskać szczegółowe instrukcje i przykłady.

### Co mam zrobić, jeśli potrzebuję wsparcia?
 Jeśli napotkasz jakiekolwiek problemy, możesz szukać pomocy na[forum wsparcia](https://forum.aspose.com/c/pdf/10).