---
title: Vykreslování událostí kalendáře v MHTML pomocí Aspose.Email
linktitle: Vykreslování událostí kalendáře v MHTML pomocí Aspose.Email
second_title: Aspose.Email .NET Email Processing API
description: Vykreslování událostí kalendáře do formátu MHTML pomocí Aspose.Email pro .NET. Naučte se krok za krokem, jak přizpůsobit a uložit soubory MSG pomocí C#.
type: docs
weight: 15
url: /cs/net/tutorials/email/handling-email-events-and-calendar/render-calendar-events-in-mhtml/
---
## Zavedení

Aspose.Email for .NET je výkonná knihovna pro zpracování úloh souvisejících s e-mailem v aplikacích .NET. Jedním z fascinujících případů použití je vykreslování událostí kalendáře programově pomocí C#. Ať už vytváříte funkci integrace kalendáře nebo vytváříte vlastní prohlížeče e-mailů, tento výukový program vás provede vykreslováním událostí kalendáře do formátu MHTML s přesností a přizpůsobením.

## Předpoklady

Než se do toho pustíme, ujistěte se, že máme vše připraveno k provedení tohoto návodu:

1.  Aspose.Email for .NET Library: Stáhněte si nejnovější verzi knihovny z[Stránka pro stahování Aspose.Email pro .NET](https://releases.aspose.com/email/net/).
2. Vývojové prostředí: Visual Studio (nebo vaše preferované IDE C#) nainstalované ve vašem systému.
3. Licence: Získejte platnou licenci pro Aspose.Email. Pro účely hodnocení můžete použít a[dočasná licence](https://purchase.aspose.com/temporary-license/).
4.  Ukázkový soubor MSG: Soubor MSG události kalendáře. Můžete použít jakýkoli`.msg` soubor s událostmi kalendáře, jako je "Schůzka s opakujícími se výskyty.msg."

## Importujte balíčky

Chcete-li začít, zahrňte do projektu potřebné jmenné prostory. 

```csharp
using System;
using Aspose.Email;
using Aspose.Email.Mht;
```

Nyní se vrhněme na průvodce krok za krokem!

## Krok 1: Načtěte soubor MSG událostí kalendáře

Nejprve načteme soubor MSG, který obsahuje událost kalendáře. Tento krok je nezbytný, protože funguje jako vstup pro vykreslení události do formátu MHTML.


```csharp
string dataDir = "Your Data Directory";
string fileName = "Meeting with Recurring Occurrences.msg";

// Načtěte soubor MSG
MailMessage msg = MailMessage.Load(dataDir + fileName);
```

- `dataDir`: Určuje adresář, kde je uložen váš soubor MSG.
- `fileName`: Název souboru události kalendáře.
- `MailMessage.Load` : Přečte soubor a načte jej do a`MailMessage` objekt.

## Krok 2: Nakonfigurujte možnosti uložení MHTML

Dále nakonfigurujeme možnosti vykreslení události kalendáře do formátu MHTML. To zahrnuje povolení konkrétních formátů, záhlaví a dalších vlastností pro přizpůsobení.

```csharp
MhtSaveOptions options = new MhtSaveOptions
{
    MhtFormatOptions = MhtFormatOptions.WriteHeader | MhtFormatOptions.RenderCalendarEvent
};
```

- `MhtSaveOptions`Představuje nastavení pro ukládání souborů MHTML.
- `MhtFormatOptions`: Konfiguruje možnosti, jako je zahrnutí záhlaví a vykreslování událostí kalendáře.

## Krok 3: Přizpůsobte si šablony zobrazení

Zde definujeme, jak by se ve výstupu měly objevit konkrétní vlastnosti, jako je čas začátku události. Tento krok umožňuje vysoce přizpůsobitelný a čitelný výstup.


```csharp
if (options.FormatTemplates.ContainsKey(MhtTemplateName.Start))
    options.FormatTemplates[MhtTemplateName.Start] = @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>";
else
    options.FormatTemplates.Add(MhtTemplateName.Start, @"<span class='headerLineTitle'>Start:</span><span class='headerLineText'>{0}</span><br/>");
```

- `MhtTemplateName.Start`: Odkazuje na vlastnost "Start" události kalendáře.
- `options.FormatTemplates`: Přizpůsobí šablonu zobrazení pro konkrétní vlastnosti.

## Krok 4: Uložte událost kalendáře jako MHTML

Nakonec uložte událost kalendáře do souboru MHTML s nakonfigurovanými možnostmi.


```csharp
msg.Save(dataDir + "Meeting with Recurring Occurrences.mhtml", options);
```

- `msg.Save`: Uloží zprávu v určeném formátu a umístění.
- `Meeting with Recurring Occurrences.mhtml`: Název výstupního souboru.

## Závěr

Vykreslování událostí kalendáře pomocí Aspose.Email pro .NET je efektivní a vysoce přizpůsobitelné. Podle výše uvedených kroků můžete bez problémů převést události kalendáře do souboru MHTML s přizpůsobeným formátováním.

## FAQ

### Co je MHTML?
MHTML je formát souboru webového archivu, který obsahuje HTML a související zdroje, jako jsou obrázky, díky čemuž je vhodný pro vykreslování a sdílení událostí kalendáře.

### Mohu vykreslit opakující se události?
Ano! Aspose.Email podporuje vykreslování opakujících se událostí a zajišťuje přesné zachycení všech detailů.

### Je vyžadována licence?
 Ano, je nutná platná licence. Můžete požádat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Mohu k výstupu přidat vlastní vlastnosti?
 Absolutně! Šablony pro další vlastnosti můžete přizpůsobit pomocí`FormatTemplates` sbírka.

### Jak mohu řešit problémy?
 Navštivte[Fórum podpory Aspose.Email](https://forum.aspose.com/c/email/12/) za odbornou pomoc.