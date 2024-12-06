---
title: Vytvořte a podepište nový řádek podpisu
linktitle: Vytvořte a podepište nový řádek podpisu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak bezproblémově přidat digitální podpis do dokumentů aplikace Word pomocí Aspose.Words for .NET. Tento komplexní výukový program pokrývá vše od nastavení prostředí a vložení řádku podpisu až po uložení a ověření podepsaných dokumentů.
type: docs
weight: 10
url: /cs/net/tutorials/words/digital-signatures/create-and-sign-new-signature-line/
---
## Zavedení

Chcete přidat digitální podpis do dokumentu aplikace Word? S Aspose.Words pro .NET je to jednodušší, než si myslíte! Tento výukový program vás provede kroky nastavení prostředí, přidání řádku podpisu a digitálního podepsání dokumentu. Začněme!

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

1.  Aspose.Words for .NET -[Stáhněte si jej zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí .NET – Visual Studio je pro tento úkol ideální.
3. Dokument k podpisu – Můžete vytvořit nový dokument aplikace Word nebo použít existující.
4.  Soubor certifikátu - A`.pfx` soubor je nezbytný pro digitální podpisy.
5. Obrázek čáry podpisu (volitelné) – Pro podpis můžete zahrnout soubor obrázku.

## Importujte požadované jmenné prostory

Chcete-li používat funkce Aspose.Words, musíte importovat následující jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;
using Aspose.Words.Signing;
```

## Krok 1: Nastavení adresáře dokumentů

Začněte definováním cesty k adresáři dokumentů. Zde budete ukládat a načítat své dokumenty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Zadejte cestu k adresáři dokumentu
```

## Krok 2: Vytvoření nového dokumentu

Dále vytvoříme nový dokument aplikace Word. Tento dokument bude sloužit jako plátno pro váš podpisový řádek.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Vložení řádku podpisu

 Nyní použijte`DocumentBuilder` třídy pro vložení řádku podpisu do dokumentu:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(new SignatureLineOptions()).SignatureLine;
```

## Krok 4: Uložení dokumentu

Po vložení řádku podpisu dokument uložte. Toto je zásadní krok před podpisem.

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLine.docx");
```

## Krok 5: Konfigurace možností podepisování

Nastavte možnosti pro proces podepisování. To zahrnuje zadání ID řádku podpisu a volitelného obrázku, který se má zobrazit s podpisem.

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    SignatureLineImage = File.ReadAllBytes(dataDir + "Enhanced Windows MetaFile.emf") // Cesta k vašemu obrazu
};
```

## Krok 6: Načtení certifikátu

Načtěte soubor certifikátu potřebný k podepsání dokumentu:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "your_certificate.pfx", "your_password"); // Upravte název souboru a heslo
```

## Krok 7: Podepsání dokumentu

 Nakonec dokument podepište pomocí`DigitalSignatureUtil` třída. Uložte podepsaný dokument pod novým názvem pro budoucí použití.

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLine.docx",
    dataDir + "SignDocuments.SignedDocument.docx", certHolder, signOptions);
```

## Závěr

Gratuluji! Úspěšně jste vytvořili dokument aplikace Word, přidali řádek podpisu a digitálně jej podepsali pomocí Aspose.Words for .NET. Tento výkonný nástroj zjednodušuje automatizaci dokumentů a zajišťuje, že vaše smlouvy a formální dokumenty budou bezpečně podepsány a ověřeny.

## FAQ

### Mohu pro řádek podpisu použít jiné formáty obrázků?

Ano, můžete použít různé formáty obrázků, včetně PNG, JPG a BMP.

###  Je nutné použít a`.pfx` file for the certificate?

 Ano, a`.pfx` soubor je standardní formát pro ukládání certifikátů a soukromých klíčů pro digitální podpisy.

### Mohu přidat více řádků podpisu do jednoho dokumentu?

Absolutně! Opakováním kroku vložení podle potřeby můžete vložit více řádků podpisu.

### Co když nemám digitální certifikát?

Budete muset získat digitální certifikát od důvěryhodné certifikační autority nebo jej vygenerovat pomocí nástrojů, jako je OpenSSL.

### Jak ověřím digitální podpis v dokumentu?

Digitální podpis můžete ověřit otevřením podepsaného dokumentu ve Wordu a kontrolou podrobností podpisu, abyste potvrdili jeho pravost a integritu.