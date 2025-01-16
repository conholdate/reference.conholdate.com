---
title: Změnit orientaci stránky PDF
linktitle: Změnit orientaci stránky PDF
second_title: Aspose.PDF pro .NET API Reference
description: Objevte, jak snadno upravit orientaci stránky souborů PDF pomocí Aspose.PDF pro .NET. Tento průvodce krok za krokem poskytuje jasné pokyny pro vkládání, otáčení a ukládání dokumentů.
type: docs
weight: 10
url: /cs/net/tutorials/pdf/master-pdf-page-management/change-pdf-page-orientation/
---
## Zavedení

Setkali jste se někdy se souborem PDF, kde je orientace stránky úplně špatná? Ať už se jedná o dokument, který byl naskenován nesprávně, nebo dokument, který jednoduše potřebuje jiné rozvržení, úprava orientace může znamenat velký rozdíl. Naštěstí Aspose.PDF for .NET nabízí výkonný a uživatelsky příjemný způsob manipulace se soubory PDF, včetně změny orientace stránek. V této příručce vás provedeme procesem krok za krokem, ať už chcete přejít z režimu na výšku na režim na šířku nebo naopak.

## Předpoklady

Než se ponoříme do podrobností, ujistěte se, že máte na místě následující:

-  Aspose.PDF for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.PDF. Pokud jste to ještě neudělali, můžete[stáhněte si to zde](https://releases.aspose.com/pdf/net/).
- Vývojové prostředí .NET: Pro vývoj .NET můžete použít Visual Studio, JetBrains Rider nebo jakékoli jiné IDE, které preferujete.
- Základní znalost C#: Znalost C# vám pomůže snadněji sledovat.
- Soubor PDF: Připravte si vzorový soubor PDF k testování. Můžete si jej vytvořit nebo si stáhnout ukázku online.

 Pokud právě začínáte, zvažte možnost vyzkoušet Aspose.PDF s a[dočasná licence zdarma](https://purchase.aspose.com/temporary-license/) než se rozhodnout[zakoupit plnou verzi](https://purchase.aspose.com/buy).

## Importovat jmenné prostory

Chcete-li manipulovat se stránkami PDF, musíte nejprve importovat potřebné jmenné prostory do svého projektu C#. Přidejte následující řádky na začátek souboru kódu:

```csharp
using System.IO;
using Aspose.Pdf;
```

Nyní, když máme vše nastaveno, můžeme začít!

## Krok 1: Načtěte dokument PDF

 Prvním krokem je načtení souboru PDF, který chcete upravit. Použijte`Document` třída z jmenného prostoru Aspose.PDF:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(Path.Combine(dataDir, "input.pdf"));
```

 Nezapomeňte vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou k vašemu souboru PDF.

## Krok 2: Projděte každou stránku

Dále projdeme každou stránku v dokumentu PDF. To nám umožňuje aplikovat změnu orientace na všechny stránky:

```csharp
foreach (Page page in doc.Pages)
{
    // Manipulujte s každou stránkou
}
```

## Krok 3: Otevřete MediaBox stránky

 Každá stránka PDF má a`MediaBox` která vymezuje její hranice. K tomu potřebujeme přístup, abychom mohli zkontrolovat aktuální orientaci a provést úpravy:

```csharp
Aspose.Pdf.Rectangle r = page.MediaBox;
```

 The`MediaBox` poskytuje rozměry stránky včetně šířky a výšky.

## Krok 4: Zaměňte šířku a výšku

Chcete-li změnit orientaci stránky, zaměníme hodnoty šířky a výšky. Tato úprava změní rozměry stránky:

```csharp
double newHeight = r.Width;
double newWidth = r.Height;
double newLLX = r.LLX;
double newLLY = r.LLY + (r.Height - newHeight);
```

Zde vypočítáme nové rozměry a přemístíme levý dolní roh (`LLY`) podle toho.

## Krok 5: Aktualizujte MediaBox a CropBox

 Nyní, když máme nové dimenze, použijeme tyto změny na`MediaBox` a`CropBox` abyste zajistili správné zobrazení stránky:

```csharp
page.MediaBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
page.CropBox = new Aspose.Pdf.Rectangle(newLLX, newLLY, newLLX + newWidth, newLLY + newHeight);
```

## Krok 6: Otočte stránku

Abychom dokončili změnu orientace, otočíme stránku. S Aspose.PDF je to jednoduché:

```csharp
page.Rotate = Rotation.on90; // Otočit o 90 stupňů
```

Tento řádek efektivně otočí stránku do požadované orientace.

## Krok 7: Uložte výstupní PDF

Po úpravě orientace všech stránek uložte aktualizovaný dokument do nového souboru:

```csharp
dataDir = dataDir + "ChangeOrientation_out.pdf";
doc.Save(dataDir);
System.Console.WriteLine("\nPage orientation changed successfully.\nFile saved at " + dataDir);
```

Nezapomeňte zadat nový název souboru, aby nedošlo k přepsání původního dokumentu.

## Závěr

A tady to máte! Změna orientace stránky souboru PDF pomocí Aspose.PDF pro .NET je jednoduchý proces. Načtením dokumentu, procházením stránek, aktualizací MediaBoxu a uložením souboru můžete snadno upravit rozvržení tak, aby vyhovovalo vašim potřebám. Ať už opravujete špatně naskenovaný dokument nebo formátujete stránky pro prezentaci, tato příručka by vám měla pomoci dokončit práci efektivně.

## FAQ

### Mohu otočit konkrétní stránky namísto všech stránek v PDF?  
Ano, smyčku můžete upravit tak, aby cílila na konkrétní stránky podle jejich indexu, místo abyste procházeli všemi stránkami.

### Co je`MediaBox`?  
 The`MediaBox` definuje velikost a tvar stránky v souboru PDF a určuje, kam je obsah umístěn.

### Funguje Aspose.PDF for .NET s jinými formáty souborů?  
Ano, Aspose.PDF si poradí s různými formáty souborů, včetně HTML, XML, XPS a dalších.

### Existuje bezplatná verze Aspose.PDF pro .NET?  
 Ano, můžete začít s a[zkušební verze zdarma](https://releases.aspose.com/) nebo požádat a[dočasná licence](https://purchase.aspose.com/temporary-license/).

### Mohu po uložení změny vrátit zpět?  
Jakmile dokument uložíte, změny jsou trvalé. Je vhodné pracovat na kopii nebo si ponechat zálohu původního souboru.