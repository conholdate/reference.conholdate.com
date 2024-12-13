---
title: Přidání nového digitálního podpisu do podepsaného souboru Excel
linktitle: Přidání nového digitálního podpisu do podepsaného souboru Excel
second_title: Aspose.Cells .NET Excel Processing API
description: Naučte se, jak přidat nový digitální podpis do existujícího podepsaného souboru Excel pomocí Aspose.Cells for .NET. Tento komplexní průvodce pokrývá všechny předpoklady, podrobné pokyny a příklad kódu.
type: docs
weight: 12
url: /cs/net/tutorials/cells/mastering-workbook-operations/adding-new-digital-signature-to-signed-excel-file/
---
## Zavedení

V dnešním digitálním prostředí je zajištění pravosti a integrity dokumentů důležitější než kdy jindy. Digitální podpisy poskytují spolehlivý způsob, jak ověřit, že dokument nebyl změněn a že pochází z legitimního zdroje. Pokud pracujete se soubory Excel v .NET a potřebujete přidat nový digitální podpis k souboru, který je již podepsaný, je tato příručka určena právě vám! Projdeme procesem přidání digitálního podpisu do existujícího podepsaného souboru Excel pomocí Aspose.Cells for .NET.

## Předpoklady

Než se pustíme do implementace, ujistěte se, že máte následující:

1.  Aspose.Cells for .NET: Stáhněte a nainstalujte Aspose.Cells z[stránka vydání](https://releases.aspose.com/cells/net/).
2. .NET Framework: Ujistěte se, že váš počítač má nastavené rozhraní .NET Framework a že jste obeznámeni se základními koncepty programování .NET.
3. Digitální certifikát: Získejte platný digitální certifikát ve formátu .pfx. Pro testování můžete vytvořit certifikát s vlastním podpisem.
4. Vývojové prostředí: K psaní a spouštění kódu C# použijte IDE, jako je Visual Studio.
5. Ukázkový soubor aplikace Excel: Mějte existující soubor aplikace Excel, který je již digitálně podepsán, což bude cílem pro přidání nového podpisu.

S těmito předpoklady se vrhneme na kód!

## Importujte potřebné balíčky

V horní části souboru C# zahrňte následující jmenné prostory pro přístup k požadovaným třídám a metodám:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
```

## Krok 1: Definujte své adresáře

Zadejte adresáře pro vaše zdrojové soubory a kam uložit výstupní soubor:

```csharp
// Zdrojový adresář
string sourceDir = "Your Document Directory"; // Nahraďte svým skutečným adresářem
// Výstupní adresář
string outputDir = "Your Document Directory"; // Nahraďte svým skutečným adresářem
```

## Krok 2: Načtěte existující podepsaný sešit

Načtěte sešit aplikace Excel, který je již podepsaný:

```csharp
// Načtěte sešit, který je již digitálně podepsán
Aspose.Cells.Workbook workbook = new Aspose.Cells.Workbook(sourceDir + "sampleDigitallySignedByCells.xlsx");
```

## Krok 3: Vytvořte sbírku digitálních podpisů

Vytvořte sbírku pro správu digitálních podpisů:

```csharp
//Vytvořte kolekci digitálních podpisů
Aspose.Cells.DigitalSignatures.DigitalSignatureCollection dsCollection = new Aspose.Cells.DigitalSignatures.DigitalSignatureCollection();
```

## Krok 4: Načtěte svůj certifikát

Načtěte svůj digitální certifikát, který bude použit k vytvoření nového podpisu:

```csharp
// Soubor certifikátu a jeho heslo
string certFileName = sourceDir + "AsposeDemo.pfx"; // Soubor vašeho certifikátu
string password = "aspose"; // Heslo vašeho certifikátu

// Vytvořte nový certifikát
System.Security.Cryptography.X509Certificates.X509Certificate2 certificate = new System.Security.Cryptography.X509Certificates.X509Certificate2(certFileName, password);
```

## Krok 5: Vytvořte nový digitální podpis

Nyní vytvořte nový digitální podpis a přidejte jej do své sbírky:

```csharp
// Vytvořte nový digitální podpis a přidejte jej do sbírky
Aspose.Cells.DigitalSignatures.DigitalSignature signature = new Aspose.Cells.DigitalSignatures.DigitalSignature(certificate, "Aspose.Cells added new digital signature in existing digitally signed workbook.", DateTime.Now);
dsCollection.Add(signature);
```

## Krok 6: Přidejte sbírku podpisů do sešitu

Přidejte kolekci digitálních podpisů do sešitu:

```csharp
// Přidejte do sešitu kolekci digitálních podpisů
workbook.AddDigitalSignature(dsCollection);
```

## Krok 7: Uložte sešit

Uložte sešit s novým digitálním podpisem, který je součástí:

```csharp
// Uložte sešit
workbook.Save(outputDir + "outputDigitallySignedByCells.xlsx");
workbook.Dispose();
```

## Krok 8: Potvrďte úspěch

Poskytněte zpětnou vazbu po úspěšném provedení:

```csharp
Console.WriteLine("Successfully added a digital signature to the existing signed Excel file.");
```

## Závěr

Gratuluji! Úspěšně jste přidali nový digitální podpis do již podepsaného souboru Excel pomocí Aspose.Cells for .NET. Tento proces zvyšuje bezpečnost vašich dokumentů a zajišťuje jejich pravost a integritu.

## FAQ

### Co je digitální podpis?

Digitální podpis je matematické schéma, které ověřuje pravost a integritu digitálních zpráv nebo dokumentů, zajišťuje, že nebyly změněny, a potvrzuje identitu podepisujícího.

### Potřebuji k vytvoření digitálního podpisu speciální certifikát?

Ano, k vytvoření platného digitálního podpisu je vyžadován digitální certifikát vydaný důvěryhodnou certifikační autoritou (CA).

### Mohu k testování použít certifikát s vlastním podpisem?

Absolutně! Pro účely vývoje a testování můžete použít certifikát s vlastním podpisem, ale pro produkční účely je vhodné použít certifikát od důvěryhodné CA.

### Co se stane, když se pokusím přidat podpis k nepodepsanému dokumentu?

Pokud se pokusíte přidat digitální podpis k dokumentu, který ještě není podepsaný, bude fungovat bez problémů, ale původní podpis nebude přítomen.

### Kde najdu více informací o Aspose.Cells?

 Podrobné návody a reference API naleznete na[Dokumentace Aspose.Cells](https://reference.aspose.com/cells/net/).