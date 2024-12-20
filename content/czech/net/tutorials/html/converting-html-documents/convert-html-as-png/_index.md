---
title: Převeďte HTML na PNG pomocí Aspose.HTML v .NET
linktitle: Převeďte HTML na PNG pomocí Aspose.HTML v .NET
second_title: Aspose.HTML .NET API pro manipulaci s HTML
description: Naučte se převádět dokumenty HTML jako obrázky PNG v .NET pomocí knihovny Aspose.HTML. Postupujte podle našeho podrobného návodu ke zjednodušení převodu HTML na obrázek.
type: docs
weight: 10
url: /cs/net/tutorials/html/converting-html-documents/convert-html-as-png/
---
## Zavedení

Chcete snadno převést dokumenty HTML na obrázky PNG? Tak to jste na správném místě! V tomto tutoriálu se ponoříme do toho, jak použít Aspose.HTML pro .NET k vykreslení HTML jako obrázků PNG. Tato výkonná knihovna zjednodušuje proces manipulace s obsahem HTML v aplikacích .NET, díky čemuž je převod webových stránek nebo šablon dokumentů do obrazových formátů hračkou.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše správně nastaveno:

1.  .NET Framework/.NET Core: Ujistěte se, že máte na svém počítači nainstalováno rozhraní .NET Framework nebo .NET Core. Můžete si stáhnout[.NET zde](https://dotnet.microsoft.com/download).

2.  Aspose.HTML for .NET Library: Budete potřebovat knihovnu Aspose.HTML. Můžete si jej stáhnout[zde](https://releases.aspose.com/html/net/) nebo to zkuste zdarma s a[zkušební verze zdarma](https://releases.aspose.com/).

3. IDE: Pro psaní a spouštění kódu se doporučuje vhodné integrované vývojové prostředí (IDE), jako je Visual Studio.

4. Základní znalost C#: Znalost programování v C# vám pomůže plynule pokračovat, ale nebojte se, vše vám vysvětlím za pochodu!

Jakmile splníte tyto předpoklady, jsme připraveni začít!

## Importujte balíčky

Abychom mohli využívat funkce Aspose.HTML, musíme importovat potřebné jmenné prostory. Zde je návod, jak přidat reference do vašeho projektu:

1. Otevřete projekt v sadě Visual Studio.
2. Klepněte pravým tlačítkem myši na svůj projekt v Průzkumníku řešení.
3. Vyberte „Spravovat balíčky NuGet“.
4.  Hledat`Aspose.HTML` a nainstalujte jej.

Jakmile budete mít balíček nainstalován, můžete začít kódovat! Prvním krokem je připravit pracovní prostor a zahrnout příslušné jmenné prostory do souboru C#.

```csharp
using Aspose.Html;
using Aspose.Html.Converters;
using Aspose.Html.Rendering;
using Aspose.Html.Rendering.Image;
```

Nyní, když jsme připravili scénu, pojďme si rozdělit proces vykreslování HTML jako obrázku PNG do podrobných a snadno pochopitelných kroků.

## Krok 1: Nastavte datový adresář

První věc, kterou chcete udělat, je nastavit adresář, kam budete obrázky ukládat. Tento adresář funguje jako domov pro generované soubory PNG.

```csharp
string dataDir = "Your Data Directory"; // Zadejte cestu k adresáři
```

-  Nahradit`"Your Data Directory"` cestou, kam chcete uložit výstupní soubory PNG. Tohle by mohlo být něco jako`@"C:\work\"`.

## Krok 2: Vytvořte objekt HTML dokumentu

Nyní, když máme nastavený adresář, vytvoříme objekt HTML dokumentu. Zde definujeme obsah HTML, který chceme převést.

```csharp
using (var document = new Aspose.Html.HTMLDocument("<style>p { color: green; }</style><p>my first paragraph</p>", dataDir))
{
    // Další kroky jdou sem
}
```

-  Ve výše uvedeném kódu inicializujeme nový`HTMLDocument` při předávání základního obsahu HTML, který stylizuje odstavec tak, aby byl zelený. Druhý parametr je cesta, kam budou uloženy případné zdroje (pokud jsou potřeba).

## Krok 3: Vytvořte HTML Renderer

 Dále vytvoříme instanci`HtmlRenderer` třída. Tato třída je zodpovědná za vykreslení našeho HTML dokumentu do požadovaného formátu obrázku.

```csharp
using (HtmlRenderer renderer = new HtmlRenderer())
{
    // Pokračujte dalším krokem
}
```

-  The`HtmlRenderer` je váš cílový objekt pro přeměnu obsahu HTML na obrázky. Zvládá proces vykreslování pod kapotou, takže se můžete soustředit na to, co potřebujete!

## Krok 4: Nastavte obrazové zařízení

 Nyní je čas na přípravu`ImageDevice`Toto je cíl pro náš proces vykreslování, kde bude vytvořen konečný obrázek PNG.

```csharp
using (ImageDevice device = new ImageDevice(dataDir + @"document_out.png"))
{
    // Vykreslete dokument HTML
}
```

- `ImageDevice` převezme úplnou cestu k souboru PNG, který má být vytvořen. Zde specifikujeme, že se má uložit jako`document_out.png` v našem dříve definovaném adresáři.

## Krok 5: Přeneste dokument HTML do formátu PNG

Nyní přichází ta vzrušující část – vykreslení našeho dokumentu HTML do obrázku PNG! Zde voláme metodu render pro dokončení převodu.

```csharp
renderer.Render(device, document);
```

-  Pomocí`Render` metoda`HtmlRenderer` , předáte`ImageDevice` a`HTMLDocument`. Tato akce převede náš určený HTML na obrázek PNG a obrázek se uloží do adresáře, který jste zadali dříve.

## Závěr

A tady to máte! Úspěšně jste vykreslili HTML jako obrázek PNG pomocí Aspose.HTML v .NET. Tento výkonný nástroj nabízí přímočarý způsob, jak programově manipulovat s obsahem HTML, čímž je generování a prezentace dokumentů snazší než kdy předtím. Ať už pracujete na webových aplikacích nebo vytváříte sestavy, tato metoda mění hru.

## FAQ

### Co je Aspose.HTML pro .NET?
Aspose.HTML for .NET je knihovna umožňující vývojářům pracovat s dokumenty HTML v aplikacích .NET a nabízí funkce pro vykreslování, konverzi a úpravy.

### Mohu používat Aspose.HTML bez licence?
Ano, Aspose nabízí bezplatnou zkušební verzi, kterou můžete použít k prozkoumání jejích funkcí před nákupem.

### Jaké typy souborů může Aspose.HTML převést?
Aspose.HTML primárně převádí HTML dokumenty do různých formátů, včetně PNG, JPEG, PDF a mnoha dalších.

### Kde mohu získat podporu pro Aspose.HTML?
 Podporu můžete získat prostřednictvím fóra Aspose[zde](https://forum.aspose.com/c/html/29).

### Je Aspose.HTML kompatibilní s .NET Core?
Ano, Aspose.HTML je kompatibilní s .NET Core a lze jej bez problémů používat v aplikacích .NET Core.