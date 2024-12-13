---
title: Dodawanie nowego podpisu cyfrowego do podpisanego pliku Excel
linktitle: Dodawanie nowego podpisu cyfrowego do podpisanego pliku Excel
second_title: Aspose.Cells .NET API przetwarzania programu Excel
description: Dowiedz się, jak dodać nowy podpis cyfrowy do istniejącego podpisanego pliku Excela za pomocą Aspose.Cells dla .NET. Ten kompleksowy przewodnik obejmuje wszystkie wymagania wstępne, instrukcje krok po kroku i przykład kodu.
type: docs
weight: 12
url: /pl/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Wstęp

W dzisiejszym cyfrowym krajobrazie zapewnienie autentyczności i integralności dokumentów jest ważniejsze niż kiedykolwiek. Podpisy cyfrowe zapewniają niezawodny sposób weryfikacji, czy dokument nie został zmieniony i czy pochodzi z legalnego źródła. Jeśli pracujesz z plikami Excel w .NET i musisz dodać nowy podpis cyfrowy do pliku, który jest już podpisany, ten przewodnik jest dla Ciebie! Przeprowadzimy Cię przez proces dodawania podpisu cyfrowego do istniejącego podpisanego pliku Excel przy użyciu Aspose.Cells dla .NET.

## Wymagania wstępne

Zanim przejdziemy do wdrożenia, upewnij się, że masz następujące rzeczy:

1.  Aspose.Cells dla .NET: Pobierz i zainstaluj Aspose.Cells z[strona wydania](https://releases.aspose.com/cells/net/).
2. .NET Framework: Upewnij się, że na Twoim komputerze jest zainstalowany .NET Framework i że znasz podstawowe koncepcje programowania .NET.
3. Certyfikat cyfrowy: Uzyskaj ważny certyfikat cyfrowy w formacie .pfx. Do testów możesz utworzyć certyfikat podpisany przez siebie.
4. Środowisko programistyczne: Użyj środowiska IDE, np. Visual Studio, do pisania i wykonywania kodu C#.
5. Przykładowy plik Excela: Posiadasz istniejący plik Excela, który jest już podpisany cyfrowo i do którego chcesz dodać nowy podpis.

Mając te wymagania wstępne na uwadze, możemy przejść do kodowania!

## Importuj niezbędne pakiety

Na górze pliku C# dodaj następujące przestrzenie nazw, aby uzyskać dostęp do wymaganych klas i metod:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Krok 1: Zdefiniuj swoje katalogi

Określ katalogi dla plików źródłowych i miejsce zapisu pliku wyjściowego:

```csharp
// Katalog źródłowy
string sourceDir = "Your Document Directory"; // Zastąp swoim aktualnym katalogiem
// Katalog wyjściowy
string outputDir = "Your Document Directory"; // Zastąp swoim aktualnym katalogiem
```

## Krok 2: Załaduj istniejący podpisany skoroszyt

Załaduj skoroszyt programu Excel, który jest już podpisany:

```csharp
// Załaduj skoroszyt, który jest już podpisany cyfrowo
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Krok 3: Utwórz kolekcję podpisów cyfrowych

Utwórz kolekcję, aby zarządzać swoimi podpisami cyfrowymi:

```csharp
//Utwórz kolekcję podpisów cyfrowych
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Krok 4: Załaduj swój certyfikat

Załaduj swój certyfikat cyfrowy, który zostanie użyty do utworzenia nowego podpisu:

```csharp
// Plik certyfikatu i jego hasło
string certFileName = sourceDir + "AsposeDemo.pfx"; // Twój plik certyfikatu
string password = "aspose"; // Hasło Twojego certyfikatu

// Utwórz nowy certyfikat
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Krok 5: Utwórz nowy podpis cyfrowy

Teraz utwórz nowy podpis cyfrowy i dodaj go do swojej kolekcji:

```csharp
// Utwórz nowy podpis cyfrowy i dodaj go do kolekcji
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Krok 6: Dodaj kolekcję podpisów do skoroszytu

Dodaj kolekcję podpisów cyfrowych do skoroszytu:

```csharp
// Dodaj kolekcję podpisów cyfrowych do skoroszytu
workbook.AddDigitalSignature(dsCollection);
```

## Krok 7: Zapisz skoroszyt

Zapisz skoroszyt z dołączonym nowym podpisem cyfrowym:

```csharp
// Zapisz skoroszyt
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Krok 8: Potwierdź powodzenie

Przekaż opinię po pomyślnym wykonaniu:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Wniosek

Gratulacje! Pomyślnie dodałeś nowy podpis cyfrowy do już podpisanego pliku Excela przy użyciu Aspose.Cells dla .NET. Ten proces zwiększa bezpieczeństwo Twoich dokumentów i zapewnia ich autentyczność i integralność.

## Najczęściej zadawane pytania

### Czym jest podpis cyfrowy?

Podpis cyfrowy to schemat matematyczny, który weryfikuje autentyczność i integralność wiadomości cyfrowych lub dokumentów, zapewniając, że nie zostały one zmienione i potwierdzając tożsamość osoby podpisującej.

### Czy potrzebuję specjalnego certyfikatu, aby utworzyć podpis cyfrowy?

Tak, do utworzenia ważnego podpisu cyfrowego wymagany jest certyfikat cyfrowy wydany przez zaufany urząd certyfikacji (CA).

### Czy mogę użyć certyfikatu podpisanego własnoręcznie do testów?

Oczywiście! Możesz użyć certyfikatu podpisanego przez siebie do celów rozwojowych i testowych, ale do produkcji zaleca się użycie certyfikatu od zaufanego CA.

### Co się stanie, jeśli spróbuję dodać podpis do niepodpisanego dokumentu?

Jeśli spróbujesz dodać podpis cyfrowy do dokumentu, który nie został jeszcze podpisany, operacja przebiegnie bez problemów, ale oryginalny podpis nie będzie obecny.

### Gdzie mogę znaleźć więcej informacji na temat Aspose.Cells?

 Aby uzyskać szczegółowe instrukcje i odniesienia do interfejsu API, sprawdź[Dokumentacja Aspose.Cells](https://reference.aspose.com/cells/net/).