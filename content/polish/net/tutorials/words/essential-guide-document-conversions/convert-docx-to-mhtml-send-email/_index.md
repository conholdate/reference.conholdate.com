---
title: Konwertuj DOCX do MHTML i wysyłaj e-maile za pomocą Aspose.Words dla .NET
linktitle: Konwertuj DOCX do MHTML i wysyłaj e-maile za pomocą Aspose.Words dla .NET
second_title: Aspose.Words API przetwarzania dokumentów
description: W tym kompleksowym przewodniku znajdziesz instrukcję krok po kroku, jak konwertować dokumenty DOCX do formatu MHTML i wysyłać je pocztą e-mail przy użyciu bibliotek Aspose.Words i Aspose.Email w środowisku .NET.
type: docs
weight: 10
url: /pl/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Wstęp

W dzisiejszym cyfrowym krajobrazie konwersja dokumentów między formatami i wysyłanie ich e-mailem to powszechne zadanie. Ten przewodnik przeprowadzi Cię przez proces konwersji pliku DOCX do formatu MHTML i wysłania go e-mailem przy użyciu potężnych bibliotek Aspose.Words i Aspose.Email dla .NET. Przedstawimy każdy krok w sposób przejrzysty, zapewniając łatwość śledzenia. Zaczynajmy!

## Wymagania wstępne

Zanim rozpoczniesz proces, upewnij się, że masz następujące ustawienia:

1.  Aspose.Words dla .NET: Pobierz i zainstaluj bibliotekę z[Strona wydań Aspose](https://releases.aspose.com/words/net/).
2.  Aspose.Email dla .NET: Pobierz i zainstaluj tę bibliotekę z[Strona wydań Aspose](https://releases.aspose.com/email/net/).
3. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework.
4. Serwer SMTP: Aby wysyłać wiadomości e-mail, potrzebny jest dostęp do serwera SMTP.

## Importowanie niezbędnych przestrzeni nazw

Aby wykorzystać Aspose.Words i Aspose.Email w swoim projekcie, musisz zaimportować wymagane przestrzenie nazw. Dodaj następujące dyrektywy using na górze pliku C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Krok 1: Załaduj dokument DOCX

 Zacznij od załadowania dokumentu DOCX, który chcesz przekonwertować. Użyj`Document` klasa z Aspose.Words, aby to osiągnąć.

```csharp
// Podaj ścieżkę do katalogu dokumentów.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 2: Zapisz dokument jako MHTML

 Następnie przekonwertuj załadowany dokument do formatu MHTML. Robi się to za pomocą`Save` metoda`Document`klasa.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Przywróć pozycję strumienia do początku w celu odczytania.
    stream.Position = 0;
}
```

## Krok 3: Utwórz wiadomość e-mail

Teraz utwórz wiadomość e-mail ze strumienia MHTML za pomocą Aspose.Email. Będziesz korzystać z`MailMessage` klasę w tym celu.

```csharp
// Załaduj strumień MHTML do wiadomości e-mail w formacie MIME Aspose.Email.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Krok 4: Wyślij e-mail

 Na koniec wyślij wiadomość e-mail za pomocą klienta SMTP. Skonfiguruj klienta SMTP za pomocą danych swojego serwera i użyj`Send` metoda wysłania wiadomości.

```csharp
// Skonfiguruj i wyślij wiadomość za pomocą Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Wniosek

Gratulacje! Udało Ci się przekonwertować dokument DOCX na MHTML i wysłać go pocztą e-mail za pomocą Aspose.Words i Aspose.Email dla .NET. Proces ten obejmuje załadowanie dokumentu, przekonwertowanie go na MHTML, utworzenie wiadomości e-mail i wysłanie jej za pomocą klienta SMTP. Dzięki tym krokom możesz bezproblemowo zautomatyzować konwersję i wysyłanie dokumentów pocztą e-mail w swoich aplikacjach.

## Najczęściej zadawane pytania

### Czy mogę użyć tej metody do konwersji innych formatów dokumentów?
Oczywiście! Aspose.Words obsługuje szeroki zakres formatów, umożliwiając konwersję DOC, DOCX, RTF i innych do MHTML.

### Jak mogę dodać załączniki do wiadomości e-mail?
 Załączniki można łatwo dodawać za pomocą`Attachments` własność`MailMessage`klasa.

### Czy Aspose.Words jest kompatybilny z .NET Core?
Tak, Aspose.Words jest kompatybilny z platformą .NET Core, dzięki czemu można go stosować w aplikacjach .NET Core.

### Czy potrzebuję licencji na Aspose.Words i Aspose.Email?
 Tak, obie biblioteki wymagają licencji. Możesz uzyskać tymczasową licencję do celów ewaluacyjnych od[Strona zakupu Aspose](https://purchase.conholdate.com/temporary-license/).

### Gdzie mogę znaleźć więcej dokumentacji?
 Aby uzyskać szczegółową dokumentację, sprawdź Aspose.Words[Tutaj](https://reference.aspose.com/words/net/) i Aspose.Email[Tutaj](https://reference.aspose.com/email/net/).