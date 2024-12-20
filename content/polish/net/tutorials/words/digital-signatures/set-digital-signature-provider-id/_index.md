---
title: Ustaw identyfikator dostawcy podpisu cyfrowego w dokumencie Word
linktitle: Ustaw identyfikator dostawcy podpisu cyfrowego w dokumencie Word
second_title: Aspose.Words API przetwarzania dokumentów
description: Dowiedz się, jak bezpiecznie dodawać podpis cyfrowy do dokumentów Word przy użyciu określonego identyfikatora dostawcy podpisu za pomocą Aspose.Words for .NET.
type: docs
weight: 10
url: /pl/net/tutorials/words/digital-signatures/set-digital-signature-provider-id/
---
## Wstęp

Cześć! Jeśli chcesz dodać podpis cyfrowy do dokumentu Word z określonym identyfikatorem dostawcy podpisu, jesteś we właściwym miejscu. Bez względu na to, czy chodzi o umowy prawne, kontrakty czy ważne dokumenty, bezpieczny podpis cyfrowy jest niezbędny. W tym samouczku przeprowadzę Cię krok po kroku przez proces ustawiania identyfikatora dostawcy podpisu w dokumencie Word przy użyciu Aspose.Words dla .NET. Zaczynajmy!

## Wymagania wstępne

Zanim zaczniesz, upewnij się, że masz następujące rzeczy:

1. Aspose.Words dla biblioteki .NET:[Pobierz tutaj](https://releases.aspose.com/words/net/).
2. Środowisko programistyczne: Visual Studio lub dowolne środowisko IDE zgodne z C#.
3.  Dokument Word: Dokument z linią podpisu (np.`Signature line.docx`).
4.  Certyfikat cyfrowy: A`.pfx` plik certyfikatu (np.`morzal.pfx`).
5. Podstawowa znajomość języka C#: Znajomość podstawowych pojęć języka C# będzie pomocna.

A teraz przejdźmy do akcji!

## Krok 1: Importuj niezbędne przestrzenie nazw

Aby rozpocząć, uwzględnij niezbędne przestrzenie nazw w swoim projekcie. Umożliwi Ci to dostęp do biblioteki Aspose.Words i powiązanych klas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.DigitalSignatures;
```

## Krok 2: Załaduj swój dokument Word

Najpierw musisz załadować dokument Word zawierający wiersz podpisu. Oto jak to zrobić:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Signature line.docx");
```

 Pamiętaj o wymianie`"YOUR DOCUMENT DIRECTORY"` z rzeczywistą ścieżką, pod którą przechowywany jest Twój dokument.

## Krok 3: Uzyskaj dostęp do linii Signature Line

Następnie uzyskaj dostęp do wiersza podpisu osadzonego w dokumencie. Wiersz podpisu jest reprezentowany jako obiekt kształtu:

```csharp
SignatureLine signatureLine = ((Shape)doc.FirstSection.Body.GetChild(NodeType.Shape, 0, true)).SignatureLine;
```

 Ten kod pobiera pierwszy kształt z treści pierwszej sekcji i rzutuje go na`SignatureLine` obiekt.

## Krok 4: Skonfiguruj opcje podpisywania

Teraz utwórzmy opcje podpisywania, które obejmują identyfikator dostawcy i identyfikator wiersza podpisu:

```csharp
SignOptions signOptions = new SignOptions
{
    ProviderId = signatureLine.ProviderId,
    SignatureLineId = signatureLine.Id
};
```

Opcje te zapewniają zastosowanie prawidłowego identyfikatora dostawcy podpisu podczas podpisywania.

## Krok 5: Załaduj certyfikat cyfrowy

 Aby podpisać dokument cyfrowo, musisz załadować swój`.pfx` plik certyfikatu:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "your_certificate_password");
```

 Zastępować`"your_certificate_password"` z aktualnym hasłem do certyfikatu, jeśli jest to możliwe.

## Krok 6: Podpisz dokument

Na koniec jesteś gotowy podpisać dokument. Użyj następującego kodu, aby wykonać operację podpisywania:

```csharp
DigitalSignatureUtil.Sign(dataDir + "Digitally signed.docx",
    dataDir + "SignDocuments.SetSignatureProviderId.docx", certHolder, signOptions);
```

 Spowoduje to podpisanie dokumentu i zapisanie go jako`Digitally signed.docx`.

## Wniosek

Gratulacje! Udało Ci się ustawić Signature Provider ID w dokumencie Word przy użyciu Aspose.Words dla .NET. Ten proces nie tylko zabezpiecza Twoje dokumenty, ale także zapewnia ich zgodność ze standardami podpisu cyfrowego. Możesz wypróbować go na własnych dokumentach!

 Jeśli masz jakieś pytania lub potrzebujesz dalszej pomocy, zapoznaj się z poniższymi często zadawanymi pytaniami lub odwiedź stronę[Forum wsparcia Aspose](https://forum.aspose.com/c/words/8).

## Najczęściej zadawane pytania

### Czym jest identyfikator dostawcy podpisu?

Identyfikator dostawcy podpisu jednoznacznie identyfikuje dostawcę podpisu cyfrowego, gwarantując autentyczność i bezpieczeństwo.

### Czy mogę podpisać się przy użyciu dowolnego pliku .pfx?

Tak, możesz użyć dowolnego ważnego certyfikatu cyfrowego. Upewnij się tylko, że masz prawidłowe hasło, jeśli jest chronione.

### Jak uzyskać plik .pfx?

Plik .pfx można uzyskać od Urzędu Certyfikacji (CA) lub wygenerować go za pomocą narzędzi takich jak OpenSSL.

### Czy można podpisać kilka dokumentów jednocześnie?

Oczywiście! Możesz przejść przez wiele dokumentów i zastosować proces podpisywania do każdego z nich.

### Co zrobić, jeśli w moim dokumencie nie ma miejsca na podpis?

Najpierw musisz wstawić linię podpisu. Aspose.Words udostępnia metody dodawania linii podpisu programowo.