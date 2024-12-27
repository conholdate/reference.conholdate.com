---
title: Změna přizpůsobení písem MHT pomocí C#
linktitle: Změna přizpůsobení písem MHT pomocí C#
second_title: Aspose.Email .NET Email Processing API
description: Naučte se, jak změnit písma během převodu MHT pomocí Aspose.Email pro .NET. Pro snadné přizpůsobení postupujte podle tohoto podrobného průvodce.
type: docs
weight: 11
url: /cs/net/tutorials/email/mastering-email-header-manipulation/changing-mht-font-customization/
---
## Zavedení

Ve světě webové komunikace jsou soubory MHT (MHTML) praktickým způsobem, jak ukládat a sdílet webový obsah, doplněný obrázky, odkazy a styly. Ale co se stane, když potřebujete vylepšit tyto soubory MHT změnou písem? Díky Aspose.Email pro .NET se tento úkol stává hračkou. V tomto tutoriálu vás krok za krokem provedeme procesem změny písem během převodu MHT. Ať už vyvíjíte aplikaci, která si poradí s formátováním e-mailů, nebo jen chcete upravit dokumenty pro vaši firmu, tato příručka vás vybaví znalostmi, které potřebujete.

## Předpoklady

Než se ponoříte do kódu, měli byste si připravit několik základních věcí:

1. Visual Studio: K práci na projektu v C# budete potřebovat integrované vývojové prostředí (IDE).
2.  Aspose.Email for .NET Library: Ujistěte se, že máte nainstalovanou knihovnu. Můžete si jej stáhnout z[odkaz](https://releases.aspose.com/email/net/).
3. .NET Framework: Váš projekt by měl být kompatibilní s .NET Framework; obvykle .NET Core nebo novější verze fungují dobře.

Máš to seřazené? Děsivý! Začněme.

## Import balíčků

Nejprve se ujistěte, že je váš projekt nastaven tak, aby používal potřebné jmenné prostory. V horní části souboru C# budete chtít zahrnout následující:

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Tools;
```

Tyto balíčky vám umožní přístup k funkcím potřebným pro práci se soubory MHT a úpravu jejich obsahu.

Nyní si rozeberme kroky spojené se změnou písem během převodu MHT.

## Krok 1: Načtěte soubor MHT

 První věc, kterou musíte udělat, je načíst soubor MHT do a`MailMessage` objekt. Zde můžete přistupovat k jeho obsahu a manipulovat s ním.

```csharp
MailMessage message = MailMessage.Load("input.mht", new MhtmlLoadOptions());
```

 Vysvětlení: Zde,`"input.mht"` je cesta k vašemu souboru MHT. The`MhtmlLoadOptions()`umožňuje nakonfigurovat, jak se soubor načítá, například jinak nakládat s přílohami nebo propojenými prostředky.

## Krok 2: Iterujte přes alternativní pohledy

Soubory MHT mají často více alternativních zobrazení, zejména pokud obsahují obsah HTML. Musíte procházet těmito pohledy, abyste našli ten, který chcete upravit.

```csharp
foreach (var alternateView in message.AlternateViews)
{
    if (alternateView.ContentType.MediaType == "text/html")
    {
        var htmlView = (AlternateView)alternateView;
        var linkedResources = htmlView.LinkedResources;
```

 Vysvětlení: Kontrolujete každého`AlternateView` zjistit, zda je typu HTML. Pokud ano, máte přístup`LinkedResources`, kde jsou obvykle uložena všechna písma propojená v HTML.

## Krok 3: Identifikujte a přizpůsobte písma

Nyní, když máte přístup k propojeným prostředkům, můžete určit, které prostředky jsou písma, a podle potřeby je upravit.

```csharp
foreach (var linkedResource in linkedResources)
{
    if (linkedResource.ContentType.MediaType == "application/x-font-ttf")
    {
        linkedResource.ContentType.Name = "Arial";  // Změňte na požadované písmo
        linkedResource.TransferEncoding = TransferEncoding.Base64;  // Ujistěte se, že je správně zakódován
    }
}
```

 Vysvětlení: Tato smyčka kontroluje, zda typ obsahu propojeného prostředku je písmo TrueType. Pokud se shoduje, můžete změnit název písma na požadovaný (jako v tomto příkladu "Arial"). The`TransferEncoding`měla by být také nastavena, aby se zajistilo správné kódování dat písem při ukládání dokumentu.

## Krok 4: Uložte aktualizovaný soubor MHT

Po přizpůsobení písem je čas uložit upravený soubor MHT. Budete se chtít ujistit, že používáte správné možnosti ukládání, abyste zachovali integritu svého souboru.

```csharp
message.Save("output.mht", SaveOptions.DefaultMhtml);
```

 Vysvětlení: V tomto řádku kódu`"output.mht"` je název souboru, do kterého chcete uložit aktualizovaný obsah. Použití`SaveOptions.DefaultMhtml` zajišťuje, že si nový soubor zachová formát MHT.

## Závěr

Změna písem v souborech MHT může výrazně zlepšit vzhled a dojem z vašich dokumentů. Využitím Aspose.Email pro .NET můžete snadno načíst soubory MHT, upravit jejich obsah a uložit změny pomocí pouhých několika řádků kódu. Ať už pracujete na osobním projektu nebo na větší aplikaci, zvládnutí těchto dovedností může zlepšit způsob prezentace informací.

## FAQ

### Co je formát MHT?
MHT je formát archivu webových stránek, který ukládá HTML dokumenty, obrázky a další zdroje do jednoho souboru.

### Mohu změnit další aspekty souborů MHT pomocí Aspose?
Absolutně! Aspose.Email vám umožňuje upravovat téměř každý aspekt souborů MHT, včetně příloh, záhlaví a dalších.

### Je Aspose.Email pro .NET zdarma?
 Aspose nabízí bezplatnou zkušební verzi, ale plná verze vyžaduje licenci. Dočasnou licenci můžete získat od[zde](https://purchase.aspose.com/temporary-license/).

### Kde najdu další dokumentaci na Aspose.Email?
 Komplexní dokumentaci a příklady naleznete na[Aspose Emailová dokumentační stránka](https://reference.aspose.com/email/net/).

### Co když při používání Aspose narazím na problémy?
 Pokud narazíte na nějaké problémy, můžete se obrátit na podporu na[Aspose fórum podpory](https://forum.aspose.com/c/email/12/).