---
title: Vlastní pořadí informací v MHTML s Aspose.Email
linktitle: Vlastní pořadí informací v MHTML s Aspose.Email
second_title: Aspose.Email .NET Email Processing API
description: V tomto podrobném návodu se dozvíte, jak definovat vlastní pořadí informací v MHTML pomocí Aspose.Email pro .NET.
type: docs
weight: 14
url: /cs/net/tutorials/email/mastering-email-header-manipulation/custom-order-of-information-in-mhtml/
---
## Zavedení

Vytváření bohatých e-mailových formátů může výrazně zlepšit komunikaci, zejména při exportu e-mailů do různých formátů souborů, jako je MHTML. Aspose.Email for .NET poskytuje vývojářům výkonnou sadu nástrojů pro manipulaci s e-maily, která zahrnuje definování vlastního pořadí pro zobrazení informací při exportu do MHTML. V této příručce rozebereme kroky potřebné k tomu, abyste toho dosáhli, abyste je mohli snadno sledovat, ať už jste zkušený vývojář nebo teprve začínáte. Tak jdeme rovnou do toho!

## Předpoklady

Než se ponoříte do definování vlastního pořadí informací v MHTML, existuje několik předpokladů, které musíte zaškrtnout ze seznamu:

1. Vývojové prostředí .NET: Ujistěte se, že máte nastavené vývojové prostředí .NET. Můžete použít Visual Studio, Visual Studio Code nebo jakékoli jiné kompatibilní IDE.

2.  Aspose.Email Library: Musíte mít nainstalovanou knihovnu Aspose.Email for .NET. Nejnovější verzi si můžete stáhnout z[Aspose stránku vydání](https://releases.aspose.com/email/net/).

3. Základní porozumění C#: Znalost programování v C# vám pomůže lépe porozumět kódu.

4.  Ukázkový e-mailový soubor: Budete potřebovat ukázku`.eml` soubor (např.`Attachments.eml`) pro testovací účely.

Jakmile budete mít tyto předpoklady, můžete se pustit do výukového programu!

## Importujte balíčky

Abyste mohli začít s kódem, budete muset importovat potřebné jmenné prostory z knihovny Aspose.Email. To je nezbytné pro přístup ke všem třídám a metodám potřebným pro manipulaci s e-mailovými soubory.

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Mhtml;
```

Zahrňte je do horní části souboru C#. Nyní jste připraveni se ponořit do kódování!

Nyní, když máte vše nastaveno, pojďme rozdělit tutoriál do zvládnutelných kroků.

## Krok 1: Nastavte svůj datový adresář

První věc, kterou musíte udělat, je vytvořit adresář, kde budou uloženy vaše e-mailové soubory. Může to být jakákoli cesta na vašem místním počítači.

```csharp
string dataDir = "Your Data Directory";
```

 Nahradit`"Your Data Directory"` se skutečnou cestou, kde jste`.eml` soubor se nachází. Pokud je například váš soubor v`C:\Emails`, napsal bys:

```csharp
string dataDir = @"C:\Emails\";
```

## Krok 2: Načtěte e-mailovou zprávu

Dále musíte načíst`.eml` soubor do a`MailMessage` objekt. To vám umožní manipulovat s obsahem a metadaty e-mailu.

```csharp
MailMessage eml = MailMessage.Load(dataDir + "Attachments.eml");
```

Ujistěte se, že název souboru odpovídá tomu, který máte v zadaném adresáři. Pokud má váš soubor jiný název, aktualizujte odpovídajícím způsobem název souboru.

## Krok 3: Nastavte možnosti uložení MHTML

S načteným e-mailem je čas definovat, jak jej chcete uložit jako MHTML. Můžete začít s výchozími možnostmi.

```csharp
MhtSaveOptions opt = SaveOptions.DefaultMhtml;
```

Tento řádek inicializuje možnosti uložení MHTML a nastavuje fázi pro pozdější přizpůsobení záhlaví.

## Krok 4: Uložte MHTML s výchozím pořadím

Uložme e-mail jako MHTML pomocí výchozího pořadí. To vám dává základní linii, se kterou můžete po úpravě porovnávat.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_1.mhtml", opt);
```

 Spusťte tento řádek a zkontrolujte zadaný adresář. Nyní byste měli vidět nový soubor MHTML s názvem`CustomOrderOfInformationInMHTML_1.mhtml`. Otevřete jej a uvidíte, jak se informace zobrazují ve výchozím nastavení.

## Krok 5: Přizpůsobte pořadí záhlaví

Nyní přichází ta zábavná část! Můžete určit, která záhlaví zahrnout do výstupu MHTML a v jakém pořadí. Začneme běžnými hlavičkami.

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.From);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
opt.RenderingHeaders.Add(MhtTemplateName.To);
opt.RenderingHeaders.Add(MhtTemplateName.Sent);
```

Přidáním těchto záhlaví sdělíte Aspose, jak chcete, aby se e-mail zobrazoval.

## Krok 6: Uložte MHTML pomocí vlastní objednávky

Po přizpůsobení záhlaví musíte e-mail znovu uložit jako MHTML, abyste viděli, jak nová objednávka ovlivní výstup.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_2.mhtml", opt);
```

 Spusťte tento kód a poté otevřete`CustomOrderOfInformationInMHTML_2.mhtml`. Porovnejte jej s prvním, abyste viděli, jak se informace změnily na základě vašeho pořadí záhlaví.

## Krok 7: Vymažte a přidejte nové pořadí záhlaví

Co když chcete úplně jiné pořadí? Můžete začít znovu vymazáním stávajícího nastavení záhlaví.

```csharp
opt.RenderingHeaders.Clear();
```

Nyní je čas definovat nové pořadí hlaviček. Pokud například chcete upřednostnit přílohy a kopírovat příjemce:

```csharp
opt.RenderingHeaders.Add(MhtTemplateName.Attachments);
opt.RenderingHeaders.Add(MhtTemplateName.Cc);
opt.RenderingHeaders.Add(MhtTemplateName.Subject);
```

## Krok 8: Uložte MHTML pomocí nové vlastní objednávky

Nakonec e-mail naposledy uložte s novým nastavením záhlaví.

```csharp
eml.Save(dataDir + "CustomOrderOfInformationInMHTML_3.mhtml", opt);
```

 Po spuštění tohoto řádku otevřete`CustomOrderOfInformationInMHTML_3.mhtml` zkontrolujte, jak prezentuje informace na základě vašeho nového přizpůsobení.

## Závěr

A tady to máte – jednoduchý průvodce definováním vlastního pořadí informací v MHTML pomocí Aspose.Email pro .NET. Pomocí těchto kroků můžete ovládat, jak jsou vaše e-maily reprezentovány ve formátu MHTML, a zajistit, že nejdůležitější informace budou prezentovány způsobem, který vyhovuje vašim potřebám. 

## FAQ

### Co je MHTML?
MHTML je zkratka pro „MIME HTML“, formát archivu webových stránek, který kombinuje HTML a další zdroje, jako jsou obrázky.

### Mohu používat Aspose.Email zdarma?
 Ano, Aspose poskytuje bezplatnou zkušební verzi, kterou mohou vývojáři prozkoumat. Můžete to najít[zde](https://releases.aspose.com/).

### Co když narazím na problémy s používáním Aspose.Email?
 Podporu od komunity můžete získat prostřednictvím[Aspose fórum](https://forum.aspose.com/c/email/12/).

### Je pro Aspose.Email k dispozici dočasná licence?
 Ano, můžete požádat o dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

### Kde mohu koupit Aspose.Email?
 Knihovnu si můžete zakoupit zde[odkaz](https://purchase.aspose.com/buy).