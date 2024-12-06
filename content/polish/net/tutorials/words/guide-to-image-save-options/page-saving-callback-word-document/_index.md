---
title: Wywołanie zwrotne zapisywania strony w dokumentach Word
linktitle: Wywołanie zwrotne zapisywania strony w dokumentach Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak łatwo przekonwertować każdą stronę dokumentu Word na pojedyncze obrazy PNG za pomocą Aspose.Words dla .NET. Ten przewodnik zawiera instrukcje krok po kroku, w tym przykłady kodu.
type: docs
weight: 10
url: /pl/net/tutorials/words/guide-to-image-save-options/page-saving-callback-word-document/
---
## Wstęp

Czy kiedykolwiek musiałeś przekonwertować każdą stronę dokumentu Word na pojedyncze obrazy? Niezależnie od tego, czy chcesz utworzyć miniatury do podglądu, czy rozbić długi raport na łatwe do przyswojenia wizualizacje, Aspose.Words dla .NET sprawia, że to zadanie jest proste i wydajne. W tym przewodniku przeprowadzimy Cię przez proces konfigurowania wywołania zwrotnego zapisywania stron, aby zapisać każdą stronę dokumentu jako obraz PNG. Zaczynajmy!

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

1.  Aspose.Words dla .NET: Pobierz i zainstaluj z[Tutaj](https://releases.aspose.com/words/net/).
2. Visual Studio: Działa każda wersja, jednak w tym przewodniku będziemy używać Visual Studio 2019.
3. Podstawowa znajomość języka C#: Znajomość języka C# pomoże Ci płynnie uczyć się języka.

## Krok 1: Importuj niezbędne przestrzenie nazw

Najpierw musimy zaimportować wymagane przestrzenie nazw. Pozwala nam to na dostęp do niezbędnych klas i metod bez konieczności wpisywania pełnej przestrzeni nazw za każdym razem.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 2: Zdefiniuj katalog dokumentów

Następnie ustaw ścieżkę do katalogu dokumentów. To tutaj znajduje się Twój dokument Word wejściowy i gdzie zostaną zapisane obrazy wyjściowe.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 3: Załaduj swój dokument

Teraz załadujmy dokument, który chcesz przetworzyć. Upewnij się, że dokument o nazwie „Rendering.docx” znajduje się w określonym katalogu.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 4: Skonfiguruj opcje zapisywania obrazu

Ustawimy opcje zapisywania obrazów, wskazując, że chcemy zapisać strony jako pliki PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Tutaj,`PageSet` definiuje zakres stron do zapisania i`PageSavingCallback` wskazuje na naszą niestandardową klasę wywołania zwrotnego.

## Krok 5: Wdróż funkcję zwrotną zapisywania strony

Teraz musimy zaimplementować klasę wywołania zwrotnego, która obsługuje sposób zapisywania każdej strony.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Ta klasa implementuje`IPageSavingCallback` interfejs. W`PageSaving` metodą określamy wzór nazewnictwa dla każdej zapisanej strony.

## Krok 6: Zapisz dokument jako obrazy

Na koniec zapisujemy dokument korzystając z skonfigurowanych opcji.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Wniosek

Gratulacje! Udało Ci się skonfigurować wywołanie zwrotne zapisywania stron, aby zapisać każdą stronę dokumentu Word jako osobny obraz PNG przy użyciu Aspose.Words dla .NET. Ta technika jest niezwykle przydatna w różnych aplikacjach, od tworzenia podglądów stron po generowanie pojedynczych obrazów stron do raportów.

## Najczęściej zadawane pytania

### Czy mogę zapisywać strony w formatach innych niż PNG?
 Tak! Możesz zapisywać strony w formatach JPEG, BMP i TIFF, zmieniając`SaveFormat` W`ImageSaveOptions`.

### Jak mogę zapisać tylko wybrane strony?
 Aby zapisać określone strony, dostosuj`PageSet` parametr w`ImageSaveOptions` aby uwzględnić tylko wybrane strony.

### Czy można dostosować jakość obrazu?
 Oczywiście! Możesz kontrolować jakość obrazu wyjściowego, ustawiając właściwości takie jak`ImageSaveOptions.JpegQuality`.

### Jak mogę wydajnie obsługiwać duże dokumenty?
W przypadku obszernych dokumentów warto rozważyć przetwarzanie stron w partiach, aby efektywnie zarządzać wykorzystaniem pamięci.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Words dla .NET?
 Aby uzyskać kompleksowe przewodniki i przykłady, zapoznaj się z[Dokumentacja Aspose.Words](https://reference.aspose.com/words/net/).