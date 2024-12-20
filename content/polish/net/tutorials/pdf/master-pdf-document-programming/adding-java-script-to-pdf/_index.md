---
title: Dodawanie skryptu Java do pliku PDF
linktitle: Dodaj plik PDF Java Script
second_title: Aspose.PDF dla .NET API Reference
description: W tym dokumencie znajdziesz kompleksowy przewodnik dotyczący dodawania interaktywnych elementów, takich jak wyskakujące okienka z alertami czy funkcje automatycznego drukowania, do dokumentów PDF przy użyciu Aspose.PDF dla platformy .NET.
type: docs
weight: 10
url: /pl/net/tutorials/pdf/master-pdf-document-programming/adding-java-script-to-pdf/
---
## Wstęp
Ten dokument zawiera kompleksowy przewodnik po dodawaniu interaktywnych elementów, takich jak alerty pop-up lub funkcje automatycznego drukowania do dokumentów PDF przy użyciu Aspose.PDF dla .NET. Wykorzystując możliwości tej biblioteki, możesz tworzyć dynamiczne i angażujące pliki PDF, które spełniają różne potrzeby użytkowników.

## Wymagania wstępne
 Przed kontynuowaniem upewnij się, że pobrałeś najnowszą wersję pliku Aspose.PDF dla platformy .NET ze strony[Wydania Aspose](https://wydania.aspose.com/pdf/net/) lub uzyskaj bezpłatną wersję próbną za pośrednictwem ich strony internetowej:[releases.aspose.com](http://releases.aspose.com).

Powinieneś również mieć podstawową wiedzę na temat języka C# i znać środowisko programistyczne, którego używasz. Ponadto, jeśli musisz unikać ograniczeń podczas procesu programistycznego, rozważ nabycie tymczasowej licencji od Aspose.

## Importowanie niezbędnych pakietów
Aby rozpocząć pisanie kodu, zaimportuj wymagane przestrzenie nazw z biblioteki Aspose.PDF:

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Annotations;
using Aspose.Pdf.Text;
```

## Krok 1: Ładowanie istniejącego pliku PDF
Załaduj istniejący dokument PDF, do którego chcesz dodać elementy interaktywne:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "input.pdf");
```

 Zastępować`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką do pliku PDF.

## Krok 2: Dodawanie JavaScript na poziomie dokumentu

 Aby zastosować skrypt, który zostanie uruchomiony po otwarciu dokumentu, utwórz wystąpienie`JavascriptAction` obiekt:

```csharp
JavascriptAction javaScript = new JavascriptAction("this.print({bUI:true,bSilent:false,bShrinkToFit:true});");
doc.OpenAction = javaScript;
```

## Krok 3: Dodawanie JavaScript na poziomie strony

 Aby wywołać określone akcje na podstawie otwierania lub zamykania stron, utwórz instancję`JavascriptAction` obiekt dla każdej strony:

```csharp
doc.Pages[2].Actions.OnOpen = new JavascriptAction("app.alert('Page 2 opened')");
doc.Pages[2].Actions.OnClose = new JavascriptAction("app.alert('Page 2 closed')");
```

## Krok 4: Zapisywanie dokumentu PDF

Aby zapisać zmodyfikowany dokument PDF, podaj ścieżkę do pliku wyjściowego:

```csharp
string dataDir = dataDir + "JavaScript-Added_out.pdf";
doc.Save(dataDir);
Console.WriteLine("\nJavaScript added successfully to the PDF.\nFile saved at " + dataDir);
```

## Wniosek
Postępując zgodnie z tym przewodnikiem i wykorzystując Aspose.PDF dla .NET, możesz skutecznie wzbogacić swoje pliki PDF o interaktywne elementy. Ta biblioteka oferuje kompleksowe rozwiązanie do tworzenia dynamicznych i angażujących dokumentów, które odpowiadają różnym potrzebom użytkowników.

## Najczęściej zadawane pytania

### Czy mogę dodać wiele akcji JavaScript do różnych stron w pliku PDF?
Tak, możesz przypisać różne akcje JavaScript poszczególnym stronom lub całemu dokumentowi.

### Czy można usunąć JavaScript z pliku PDF po jego dodaniu?
 Tak, możesz usunąć lub zmodyfikować istniejące akcje JavaScript, czyszcząc`Actions` Właściwości dokumentu lub strony.

### Jakich funkcji JavaScript mogę używać w pliku PDF?
Można używać dowolnego języka JavaScript obsługiwanego przez moduł JavaScript programu Adobe Acrobat, takiego jak drukowanie, alerty i manipulacje formularzami.

### Czy JavaScript działa we wszystkich przeglądarkach PDF?
Większość akcji JavaScript będzie działać w przeglądarkach PDF obsługujących interaktywne pliki PDF, takich jak Adobe Acrobat. Jednak niektóre podstawowe czytniki PDF mogą nie obsługiwać JavaScript.