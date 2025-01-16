---
title: Pokročilé přizpůsobení grafu pomocí Aspose.Slides pro .NET
linktitle: Pokročilé přizpůsobení grafu pomocí Aspose.Slides pro .NET
second_title: Aspose.Slides .NET PowerPoint Processing API
description: Odemkněte plný potenciál Aspose.Slides pro .NET zvládnutím pokročilých technik přizpůsobení grafů. Tento podrobný průvodce pokrývá vše od základní tvorby grafu až po složité detaily, jako jsou čáry mřížky, názvy os a vlastní barvy.
type: docs
weight: 10
url: /cs/net/tutorials/slides/master-advanced-chart-customization/advanced-chart-customization/
---
## Zavedení

Vytváření vizuálně přitažlivých a informativních grafů je zásadní pro efektivní prezentaci dat. Aspose.Slides for .NET nabízí výkonné nástroje pro přizpůsobení grafů, které vám umožní přizpůsobit každý aspekt vašich grafů. V tomto tutoriálu prozkoumáme pokročilé techniky pro přizpůsobení grafů pomocí Aspose.Slides pro .NET.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:

1.  Aspose.Slides for .NET Library: Stáhněte si a nainstalujte knihovnu Aspose.Slides z[zde](https://releases.aspose.com/slides/net/).
2. Vývojové prostředí .NET: Nastavte vývojové prostředí .NET, jako je Visual Studio.
3. Základní znalost C#: Prospěšná bude znalost programování v C#, protože budeme psát kód C#.

Nyní si rozdělíme pokročilý proces přizpůsobení grafu do jasných kroků.

## Krok 1: Vytvořte novou prezentaci

Začněte vytvořením nové prezentace, do které bude graf uložen.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "Your Document Directory";

// Vytvořte adresář, pokud neexistuje.
if (!System.IO.Directory.Exists(dataDir))
    System.IO.Directory.CreateDirectory(dataDir);

// Spusťte prezentaci
Presentation pres = new Presentation();
```

## Krok 2: Otevřete první snímek

Dále přejděte na první snímek, kam chcete přidat graf.

```csharp
// Otevřete první snímek
ISlide slide = pres.Slides[0];
```

## Krok 3: Přidejte vzorový graf

Nyní přidáme na snímek spojnicový graf se značkami.

```csharp
// Přidejte ukázkový graf
IChart chart = slide.Shapes.AddChart(ChartType.LineWithMarkers, 50, 50, 500, 400);
```

## Krok 4: Nastavte nadpis grafu

Nastavení názvu grafu poskytuje základní kontext.

```csharp
// Nastavte název grafu
chart.HasTitle = true;
chart.ChartTitle.AddTextFrameForOverriding("");
IPortion chartTitle = chart.ChartTitle.TextFrameForOverriding.Paragraphs[0].Portions[0];
chartTitle.Text = "Sample Chart";
chartTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
chartTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
chartTitle.PortionFormat.FontHeight = 20;
chartTitle.PortionFormat.FontBold = NullableBool.True;
chartTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Krok 5: Přizpůsobte hlavní čáry mřížky

Pro lepší čitelnost můžete vylepšit čáry mřížky pro osu hodnot.

```csharp
// Přizpůsobte hlavní čáry mřížky pro osu hodnot
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Blue;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.Width = 5;
chart.Axes.VerticalAxis.MajorGridLinesFormat.Line.DashStyle = LineDashStyle.DashDot;
```

## Krok 6: Přizpůsobte vedlejší čáry mřížky

Podobně přizpůsobte vedlejší čáry mřížky pro osu hodnot.

```csharp
// Přizpůsobte vedlejší čáry mřížky pro osu hodnot
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Red;
chart.Axes.VerticalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Krok 7: Definujte formát čísla osy hodnot

Čísla zobrazená na ose hodnot můžete formátovat.

```csharp
// Nastavte formát čísla osy hodnot
chart.Axes.VerticalAxis.IsNumberFormatLinkedToSource = false;
chart.Axes.VerticalAxis.DisplayUnit = DisplayUnitType.Thousands;
chart.Axes.VerticalAxis.NumberFormat = "0.0%";
```

## Krok 8: Nastavte maximální a minimální hodnoty

Definujte maximální a minimální hodnoty pro graf.

```csharp
// Nastavte maximální a minimální hodnoty grafu
chart.Axes.VerticalAxis.IsAutomaticMajorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMaxValue = false;
chart.Axes.VerticalAxis.IsAutomaticMinorUnit = false;
chart.Axes.VerticalAxis.IsAutomaticMinValue = false;

chart.Axes.VerticalAxis.MaxValue = 15f;
chart.Axes.VerticalAxis.MinValue = -2f;
chart.Axes.VerticalAxis.MinorUnit = 0.5f;
chart.Axes.VerticalAxis.MajorUnit = 2.0f;
```

## Krok 9: Přizpůsobte vlastnosti textu osy hodnot

Vylepšení vlastností textu osy hodnot zlepšuje čitelnost.

```csharp
// Přizpůsobte vlastnosti textu osy hodnot
IChartPortionFormat txtVal = chart.Axes.VerticalAxis.TextFormat.PortionFormat;
txtVal.FontBold = NullableBool.True;
txtVal.FontHeight = 16;
txtVal.FontItalic = NullableBool.True;
txtVal.FillFormat.FillType = FillType.Solid;
txtVal.FillFormat.SolidFillColor.Color = Color.DarkGreen;
txtVal.LatinFont = new FontData("Times New Roman");
```

## Krok 10: Přidejte název osy hodnoty

Přidáním názvu k ose hodnot můžete objasnit, co data představují.

```csharp
// Nastavit název osy hodnot
chart.Axes.VerticalAxis.HasTitle = true;
chart.Axes.VerticalAxis.Title.AddTextFrameForOverriding("");
IPortion valTitle = chart.Axes.VerticalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
valTitle.Text = "Primary Axis";
valTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
valTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
valTitle.PortionFormat.FontHeight = 20;
valTitle.PortionFormat.FontBold = NullableBool.True;
valTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Krok 11: Přizpůsobte hlavní čáry mřížky pro osu kategorie

Nyní vylepšeme hlavní čáry mřížky pro osu kategorií.

```csharp
// Přizpůsobte hlavní čáry mřížky pro osu kategorie
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Green;
chart.Axes.HorizontalAxis.MajorGridLinesFormat.Line.Width = 5;
```

## Krok 12: Upravte vedlejší čáry mřížky pro osu kategorie

Podobně přizpůsobte vedlejší čáry mřížky pro osu kategorie.

```csharp
// Přizpůsobte vedlejší čáry mřížky pro osu kategorie
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.FillType = FillType.Solid;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.FillFormat.SolidFillColor.Color = Color.Yellow;
chart.Axes.HorizontalAxis.MinorGridLinesFormat.Line.Width = 3;
```

## Krok 13: Přizpůsobte vlastnosti textu osy kategorie

Vylepšete styl písma a vzhled popisků os kategorií.

```csharp
// Přizpůsobte vlastnosti textu osy kategorie
IChartPortionFormat txtCat = chart.Axes.HorizontalAxis.TextFormat.PortionFormat;
txtCat.FontBold = NullableBool.True;
txtCat.FontHeight = 16;
txtCat.FontItalic = NullableBool.True;
txtCat.FillFormat.FillType = FillType.Solid;
txtCat.FillFormat.SolidFillColor.Color = Color.Blue;
txtCat.LatinFont = new FontData("Arial");
```

## Krok 14: Přidejte název osy kategorie

V případě potřeby můžete také přidat název pro osu kategorií.

```csharp
// Nastavte název osy kategorie
chart.Axes.HorizontalAxis.HasTitle = true;
chart.Axes.HorizontalAxis.Title.AddTextFrameForOverriding("");
IPortion catTitle = chart.Axes.HorizontalAxis.Title.TextFrameForOverriding.Paragraphs[0].Portions[0];
catTitle.Text = "Sample Category";
catTitle.PortionFormat.FillFormat.FillType = FillType.Solid;
catTitle.PortionFormat.FillFormat.SolidFillColor.Color = Color.Gray;
catTitle.PortionFormat.FontHeight = 20;
catTitle.PortionFormat.FontBold = NullableBool.True;
catTitle.PortionFormat.FontItalic = NullableBool.True;
```

## Krok 15: Další přizpůsobení

Vylepšete svůj graf pomocí dalších přizpůsobení, jako jsou legendy, barvy stěn a nastavení plochy.

```csharp
// Další přizpůsobení (volitelné)

// Přizpůsobte vlastnosti textu legend
IChartPortionFormat txtLeg = chart.Legend.TextFormat.PortionFormat;
txtLeg.FontBold = NullableBool.True;
txtLeg.FontHeight = 16;
txtLeg.FontItalic = NullableBool.True;
txtLeg.FillFormat.FillType = FillType.Solid;
txtLeg.FillFormat.SolidFillColor.Color = Color.DarkRed;

// Zobrazit legendy grafu bez překrývajících se grafů
chart.Legend.Overlay = true;

// Nastavení barvy zadní stěny grafu
chart.BackWall.Thickness = 1;
chart.BackWall.Format.Fill.FillType = FillType.Solid;
chart.BackWall.Format.Fill.SolidFillColor.Color = Color.Orange;

// Nastavit barvu podlahy grafu
chart.Floor.Format.Fill.FillType = FillType.Solid;
chart.Floor.Format.Fill.SolidFillColor.Color = Color.Red;

// Nastavte barvu oblasti plotru
chart.PlotArea.Format.Fill.FillType = FillType.Solid;
chart.PlotArea.Format.Fill.SolidFillColor.Color = Color.LightCyan;

// Uložte prezentaci
pres.Save(dataDir + "FormattedChart_out.pptx", SaveFormat.Pptx);
```

## Závěr

V tomto komplexním průvodci jsme se zabývali pokročilými technikami přizpůsobení grafů pomocí Aspose.Slides pro .NET. Naučili jste se vytvořit prezentaci, přidat graf, upravit jeho vzhled a přizpůsobit různé prvky grafu, jako jsou čáry mřížky, popisky os a legendy. 

## FAQ

### Jaké verze .NET jsou podporovány Aspose.Slides pro .NET?
Aspose.Slides for .NET podporuje různé verze .NET, včetně .NET Framework a .NET Core. Úplný seznam podporovaných verzí naleznete v dokumentaci.

### Mohu vytvářet grafy ze zdrojů dat, jako jsou soubory aplikace Excel?
Ano, Aspose.Slides vám umožňuje vytvářet grafy z externích zdrojů dat, jako jsou tabulky aplikace Excel. Podrobné příklady naleznete v dokumentaci.

### Jak mohu do řady grafů přidat vlastní štítky dat?
 Chcete-li přidat vlastní štítky dat, přejděte na`DataLabels` vlastnost série a přizpůsobte štítky podle potřeby. Ukázky kódu najdete v dokumentaci.

### Je možné exportovat graf do různých formátů, jako je PDF nebo obrázky?
Absolutně! Aspose.Slides umožňuje exportovat vaše prezentace s grafy do různých formátů, včetně PDF a obrazových formátů.

### Kde najdu další návody a příklady pro Aspose.Slides pro .NET?
 Navštivte Aspose.Slides[webové stránky](https://reference.aspose.com/slides/net/) pro rozsáhlé výukové programy, příklady kódu a dokumentaci.