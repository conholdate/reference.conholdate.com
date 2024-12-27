---
title: Śledź postęp konwersji wiadomości e-mail za pomocą Aspose.Email dla .NET
linktitle: Śledź postęp konwersji wiadomości e-mail za pomocą Aspose.Email dla .NET
second_title: Aspose.Email .NET API przetwarzania poczty e-mail
description: Dowiedz się, jak krok po kroku śledzić postęp konwersji wiadomości e-mail w języku C#, korzystając z Aspose.Email dla .NET. Zwiększ wydajność swojego projektu dzięki temu szczegółowemu samouczkowi.
type: docs
weight: 12
url: /pl/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Wstęp

Efektywne zarządzanie dokumentami e-mail często wiąże się ze śledzeniem postępu ich konwersji. Aspose.Email dla .NET zapewnia solidne narzędzia do realizacji tego celu, umożliwiając deweloperom bezproblemową obsługę operacji e-mail. Ten samouczek zagłębia się w to, jak można śledzić postęp konwersji dokumentów e-mail w C#, rozbijając proces krok po kroku dla łatwości zrozumienia.  

## Wymagania wstępne  

Zanim przejdziemy do samouczka, upewnijmy się, że wszystko jest skonfigurowane:  

1.  Aspose.Email dla .NET: Pobierz i zainstaluj[Aspose.Email dla .NET](https://releases.aspose.com/email/net/) biblioteka.  
2. Środowisko programistyczne: zainstaluj program Visual Studio lub inne środowisko programistyczne zgodne z platformą .NET.  
3. .NET Framework: Upewnij się, że zainstalowany jest .NET Framework 4.5 lub nowszy.  
4.  Licencja tymczasowa: Rozważ uzyskanie[licencja tymczasowa](https://purchase.aspose.com/temporary-license/) aby zapoznać się ze wszystkimi funkcjami Aspose.Email.  
5.  Przykładowy plik e-maila: Przygotuj`.eml` plik (np.`test.eml`) do wykorzystania jako próbka.  

## Importuj pakiety  

Aby użyć Aspose.Email w swoim projekcie, musisz zaimportować wymagane przestrzenie nazw. Dodaj następujące polecenia using na górze pliku:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Krok 1: Skonfiguruj swój projekt  

Zacznij od utworzenia nowej aplikacji konsoli C# w Visual Studio. Będzie ona stanowić podstawę do wdrożenia śledzenia konwersji dokumentów e-mail.  
  
1. Otwórz program Visual Studio i utwórz nowy projekt aplikacji konsolowej.  
2. Zainstaluj pakiet NuGet Aspose.Email:  
```sh
Install-Package Aspose.Email
```  
3.  Dodaj`.eml` plik do katalogu swojego projektu.  

## Krok 2: Załaduj plik e-mail  

 Teraz załaduj plik e-mail do`MailMessage` obiekt. To pierwszy krok w pracy z danymi e-mail.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`:Określa katalog, w którym znajduje się plik wiadomości e-mail.  
- `MailMessage.Load` :Czyta`.eml` plik i przygotowuje go do dalszych operacji.  

## Krok 3: Zainicjuj strumień pamięci  

 Następnie utwórz`MemoryStream` obiekt umożliwiający tymczasowe przechowywanie przekonwertowanych danych e-mail.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 A`MemoryStream` służy tutaj do zarządzania wynikami procesu konwersji bez zapisywania danych bezpośrednio na dysku.  

## Krok 4: Zdefiniuj opcje konwersji  

 Skonfiguruj`EmlSaveOptions` z niestandardowym modułem śledzenia postępu konwersji.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Określa format wyjściowy.  
- `CustomProgressHandler`: Przypisuje niestandardową funkcję obsługi w celu monitorowania postępu.  

## Krok 5: Zapisz wiadomość e-mail w strumieniu pamięci  

Zapisz`MailMessage` obiekt przy użyciu określonych opcji, włączając funkcjonalność śledzenia postępu.  
 
```csharp
msg.Save(ms, opt);
```
 
Ten krok rozpoczyna proces konwersji wiadomości e-mail i wysyła aktualizacje do programu obsługującego postęp.  

## Krok 6: Wdróż program obsługi postępu  

 Zdefiniuj`ShowEmlConversionProgress` metoda obsługi aktualizacji postępu i wyświetlania ich w konsoli.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`:Zawiera szczegółowe informacje o procesie konwersji.  
-  Przełącz przypadki: obsługuj różne etapy konwersji:`MimeStructureCreated`, `MimePartSaved` , I`SavedToStream`.  

### Czego się spodziewać?  
W miarę postępu konwersji na konsoli będą drukowane szczegółowe aktualizacje, takie jak:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Wniosek  

Śledzenie postępu konwersji dokumentów e-mail w C# nigdy nie było łatwiejsze dzięki Aspose.Email dla .NET. Dzięki temu samouczkowi nauczyłeś się, jak załadować plik e-mail, skonfigurować obsługę postępu i zapisać dane e-mail, monitorując cały proces. Ta funkcjonalność zapewnia, że będziesz informowany i będziesz mieć kontrolę podczas operacji na dokumencie e-mail.  

## Najczęściej zadawane pytania  

###  Czy mogę użyć tego kodu w innych formatach niż`.eml`?  
 Tak, zmodyfikuj`MailMessageSaveType`aby dostosować się do innych formatów, takich jak MSG lub MHTML.  

### Jak radzić sobie z dużymi plikami e-mail?  
 Rozważ użycie`FileStream` zamiast`MemoryStream` dla lepszej wydajności w przypadku dużych plików.  

### Czym jest licencja tymczasowa i jak mogę ją uzyskać?  
 Tymczasowa licencja pozwala bezpłatnie ocenić pełne funkcje biblioteki. Pobierz ją[Tutaj](https://purchase.aspose.com/temporary-license/).  

### Czy mogę zintegrować ten kod z aplikacją internetową?  
Tak, kod jest kompatybilny z aplikacjami internetowymi wykorzystującymi ASP.NET lub podobne frameworki.  

### Gdzie mogę znaleźć dodatkowe materiały?  
 Sprawdź[dokumentacja](https://reference.aspose.com/email/net/) lub odwiedź[forum wsparcia](https://forum.aspose.com/c/email/12/) po pomoc.  