---
title: Vykreslování dokumentu s komentáři
linktitle: Vykreslování dokumentu s komentáři
second_title: GroupDocs.Viewer .NET API
description: Tento komplexní výukový program poskytuje podrobné pokyny k vykreslování dokumentů s komentáři v aplikacích .NET pomocí knihovny GroupDocs.Viewer.
type: docs
weight: 13
url: /cs/net/tutorials/viewer/mastering-render-options/rendering-document-comments/
---
## Zavedení

GroupDocs.Viewer for .NET je robustní knihovna navržená tak, aby umožnila vývojářům vykreslování dokumentů pro různé formáty. Ať už potřebujete zobrazit dokumenty aplikace Word, tabulky Excel, prezentace PowerPoint nebo soubory PDF, GroupDocs.Viewer zjednodušuje proces integrace. V tomto tutoriálu vás provedeme kroky nezbytnými k vykreslení dokumentů s komentáři, čímž zajistíme, že budete důkladně rozumět každému příslušnému aspektu.

## Předpoklady
Než se ponoříme do specifik vykreslování dokumentů s komentáři, ujistěte se, že máte nastaveno následující:

### Vývojové prostředí .NET
Ujistěte se, že máte připravené vývojové prostředí pro .NET. Budete potřebovat kompatibilní IDE, jako je Visual Studio, spolu s .NET SDK nainstalovaným na vašem počítači.

### GroupDocs.Viewer pro instalaci .NET
GroupDocs.Viewer for .NET si můžete stáhnout a nainstalovat z webu nebo přímo přes tento odkaz:
[Stáhněte si GroupDocs.Viewer pro .NET](https://releases.groupdocs.com/viewer/net/)

## Importovat jmenné prostory
Začněte importováním potřebných jmenných prostorů do vašeho projektu .NET. Tento krok vám uděluje přístup ke třídám a metodám potřebným pro vykreslování dokumentů.

```csharp
using System;
using System.IO;
using GroupDocs.Viewer.Options;
```

## Krok 1: Definujte výstupní adresář
Vyberte výstupní adresář, do kterého se uloží vykreslený dokument s komentáři.

```csharp
string outputDirectory = @"C:\Your\Document\Directory"; // Zadejte cestu k adresáři
```

## Krok 2: Definujte formát cesty k souboru stránky
Nastavte formát cesty k souboru pro jednotlivé stránky vykreslovaného dokumentu.

```csharp
string pageFilePathFormat = Path.Combine(outputDirectory, "page_{0}.html");
```

## Krok 3: Vytvořte instanci objektu prohlížeče
 Vytvořte instanci souboru`Viewer` třídy, předáním cesty k vašemu dokumentu, který obsahuje komentáře.

```csharp
using (Viewer viewer = new Viewer(@"C:\Path\To\Your\DocumentWithComments.docx"))
{
    // Pokračujte v konfiguraci možností vykreslování
}
```

## Krok 4: Nakonfigurujte možnosti vykreslování
Nastavte možnosti vykreslování a ujistěte se, že je povoleno zobrazení vložených zdrojů a komentářů.

```csharp
HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources(pageFilePathFormat);
options.RenderComments = true; // Povolit vykreslování komentářů
```

## Krok 5: Vykreslení dokumentu s komentáři
 Zavolejte na`View` metoda na`Viewer` objekt s nakonfigurovanými možnostmi.

```csharp
viewer.View(options);
```

## Krok 6: Zobrazte zprávu o úspěchu
Po procesu vykreslování poskytněte uživateli zpětnou vazbu.

```csharp
Console.WriteLine($"\nSource document rendered successfully.\nCheck output in {outputDirectory}.");
```

## Závěr
V tomto tutoriálu jste se naučili vykreslovat dokumenty s komentáři pomocí GroupDocs.Viewer for .NET. Dodržováním nastíněných kroků můžete snadno začlenit funkce vykreslování dokumentů do svých aplikací a zlepšit tak uživatelskou zkušenost.

## FAQ

### Dokáže GroupDocs.Viewer zvládnout složité formátování dokumentů?
Ano, GroupDocs.Viewer efektivně vykresluje dokumenty obsahující různé formátovací prvky, včetně tabulek, obrázků a vlastních písem.

### Je GroupDocs.Viewer kompatibilní s více formáty dokumentů?
Absolutně! Knihovna podporuje širokou škálu formátů, jako jsou PDF, DOCX, XLSX, PPTX a mnoho dalších.

### Mohu přizpůsobit možnosti vykreslování tak, aby vyhovovaly konkrétním potřebám?
Ano, GroupDocs.Viewer poskytuje řadu flexibilních možností vykreslování pro přizpůsobení výstupů podle požadavků vaší aplikace.

### Mohu vykreslit dokumenty z externích zdrojů?
Ano, knihovna umožňuje vykreslování dokumentů z různých zdrojů, včetně místních cest k souborům, streamů a adres URL.

### Je k dispozici zkušební verze GroupDocs.Viewer?
Ano, můžete začít prozkoumávat GroupDocs.Viewer pomocí bezplatné zkušební verze a vyhodnotit jeho funkce a možnosti.