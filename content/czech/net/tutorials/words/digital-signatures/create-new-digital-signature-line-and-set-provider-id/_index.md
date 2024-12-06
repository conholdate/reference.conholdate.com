---
title: Vytvořte novou linku digitálního podpisu a nastavte ID poskytovatele
linktitle: Vytvořte novou linku digitálního podpisu a nastavte ID poskytovatele
second_title: Aspose.Words API pro zpracování dokumentů
description: Zjistěte, jak programově přidávat podpisové řádky do dokumentů aplikace Word pomocí Aspose.Words for .NET. Tento komplexní průvodce pokrývá vše od nastavení vývojového prostředí po vkládání podpisových řádků a bezpečné podepisování dokumentů.
type: docs
weight: 10
url: /cs/net/tutorials/words/digital-signatures/create-new-digital-signature-line-and-set-provider-id/
---
## Zavedení

Ahoj, tech nadšenci! Chtěli jste někdy automatizovat zahrnutí podpisových řádků do dokumentů aplikace Word? Dnes se ponoříme do toho, jak toho dosáhnout pomocí Aspose.Words pro .NET. Tento podrobný průvodce vás provede vytvořením řádku podpisu a nastavením ID poskytovatele, díky čemuž budou vaše úlohy zpracování dokumentů efektivnější a efektivnější.

## Předpoklady

Než do toho skočíme, ujistěte se, že máte vše nastaveno:

1.  Aspose.Words for .NET: Pokud jste ji ještě nenainstalovali, stáhněte si ji[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Použijte Visual Studio nebo jakékoli vývojové nastavení C#.
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
4. Certifikát PFX: K podepisování dokumentů budete potřebovat certifikát PFX, který lze získat od důvěryhodné certifikační autority.

## Import nezbytných jmenných prostorů

Chcete-li začít, importujte požadované jmenné prostory do svého projektu C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Signing;
using System;
```

Nyní se pojďme ponořit do podrobností o vytvoření nového řádku podpisu a nastavení ID poskytovatele.

## Krok 1: Vytvořte nový dokument

Nejprve musíme vytvořit nový dokument Word, který bude sloužit jako plátno pro náš podpisový řádek:

```csharp
// Zadejte cestu k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde inicializujeme nový`Document` a a`DocumentBuilder`, což nám umožňuje snadno přidávat prvky.

## Krok 2: Definujte možnosti podpisové linky

Dále definujeme možnosti pro náš podpisový řádek, včetně jména podepsaného, titulu, e-mailu a dalších relevantních podrobností:

```csharp
SignatureLineOptions signatureLineOptions = new SignatureLineOptions
{
    Signer = "vderyushev",
    SignerTitle = "QA",
    Email = "vderyushev@aspose.com",
    ShowDate = true,
    DefaultInstructions = false,
    Instructions = "Please sign here.",
    AllowComments = true
};
```

Tyto možnosti pomáhají personalizovat linii podpisů a činí ji jasnou a profesionální.

## Krok 3: Vložte řádek podpisu

S připravenými možnostmi nyní můžeme do dokumentu vložit řádek podpisu:

```csharp
SignatureLine signatureLine = builder.InsertSignatureLine(signatureLineOptions).SignatureLine;
signatureLine.ProviderId = Guid.Parse("CF5A7BB4-8F3C-4756-9DF6-BEF7F13259A2");
```

 The`InsertSignatureLine`metoda přidá řádek podpisu a my mu přiřadíme jedinečné ID poskytovatele.

## Krok 4: Uložte dokument

Po vložení řádku podpisu dokument uložíme:

```csharp
doc.Save(dataDir + "SignDocuments.SignatureLineProviderId.docx");
```

Tím se dokument uloží s nově přidaným řádkem podpisu.

## Krok 5: Nastavte možnosti podepisování

Nyní nakonfigurujeme možnosti podepisování, včetně ID řádku podpisu, ID poskytovatele, komentářů a času podpisu:

```csharp
SignOptions signOptions = new SignOptions
{
    SignatureLineId = signatureLine.Id,
    ProviderId = signatureLine.ProviderId,
    Comments = "Document was signed by vderyushev",
    SignTime = DateTime.Now
};
```

Tato nastavení zajistí, že dokument bude podepsán se správnými detaily.

## Krok 6: Vytvořte držitele certifikátu

K podpisu dokumentu musíme vytvořit držitele certifikátu pomocí certifikátu PFX:

```csharp
CertificateHolder certHolder = CertificateHolder.Create(dataDir + "morzal.pfx", "aw");
```

 Nahradit`"morzal.pfx"` se skutečným názvem souboru certifikátu a`"aw"` s heslem k certifikátu.

## Krok 7: Podepište dokument

Nakonec dokument podepíšeme pomocí nástroje pro digitální podpis:

```csharp
DigitalSignatureUtil.Sign(dataDir + "SignDocuments.SignatureLineProviderId.docx", 
    dataDir + "SignDocuments.CreateNewSignatureLineAndSetProviderId.docx", certHolder, signOptions);
```

Tento proces podepíše dokument a uloží jej jako nový soubor.

## Závěr

Gratuluji! Úspěšně jste vytvořili řádek podpisu a nastavili ID poskytovatele v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná knihovna zjednodušuje úlohy zpracování dokumentů a zefektivňuje váš pracovní postup. Vyzkoušejte to a uvidíte, jak to může zlepšit vaše projekty!

## FAQ

### Mohu přizpůsobit vzhled řádku podpisu?
 Absolutně! Můžete upravit různé možnosti v`SignatureLineOptions` aby vyhovovaly vašemu stylu a požadavkům.

### Co když nemám certifikát PFX?
Budete jej muset získat od důvěryhodné certifikační autority, protože je nezbytný pro digitální podepisování dokumentů.

### Mohu do dokumentu přidat více řádků podpisu?
Ano, můžete přidat více řádků podpisu opakováním procesu vkládání s různými možnostmi.

### Je Aspose.Words for .NET kompatibilní s .NET Core?
Ano, Aspose.Words for .NET podporuje .NET Core, takže je univerzální pro různá vývojová prostředí.

### Jak bezpečné jsou digitální podpisy?
Digitální podpisy vytvořené pomocí Aspose.Words jsou vysoce bezpečné za předpokladu, že používáte platný a důvěryhodný certifikát.