---
title: Přidání obsahu do dokumentu PDF
linktitle: Přidání obsahu do dokumentu PDF
second_title: Aspose.PDF pro .NET API Reference
description: Tento tutoriál ukazuje, jak přidat obsah (TOC) do dokumentu PDF pomocí Aspose.Pdf pro .NET.
type: docs
weight: 40
url: /cs/net/tutorials/pdf/master-pdf-document-programming/adding-toc-to-pdf/
---
## Zavedení

Vytvoření obsahu (TOC) v dokumentu PDF může výrazně zlepšit jeho navigaci a dostupnost. V této příručce si ukážeme, jak přidat TOC do souboru PDF pomocí Aspose.Pdf pro .NET.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

1.   Aspose.PDF pro .NET: Stáhněte a nainstalujte nejnovější verzi z[zde](https://releases.aspose.com/pdf/net/).
2.  Vývojové prostředí: Nastavte vývojové prostředí .NET, jako je Visual Studio.
3.   Licence: V případě potřeby si vyžádejte dočasnou licenci; prosím navštivte[Licenční stránka Aspose.Pdf](https://asposepdf.com/developers) pro více informací.

Import nezbytných knihoven

```csharp
using System.IO;
using System;
using Aspose.Pdf;
using Aspose.Pdf.Text;
```

## Krok 1: Načtěte dokument PDF

Načtěte svůj stávající soubor PDF, kam chcete přidat obsah. Zadejte cestu k adresáři dokumentů.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "AddTOC.pdf");
```

## Krok 2: Vložte novou stránku pro TOC

Vložte novou stránku na začátek dokumentu PDF. Tato stránka bude sloužit jako obsah (TOC).

```csharp
Page tocPage = doc.Pages.Insert(1);
```

## Krok 3: Vytvořte objekt TOC Information Object

Vytvořte objekt, který bude představovat informace TOC. Pro lepší navigaci přidejte název a odkaz na něj.

```csharp
TocInfo tocInfo = new TocInfo();
TextFragment title = new TextFragment("Table Of Contents");
title.TextState.FontSize = 20;
title.TextState.FontStyle = FontStyles.Bold;
tocInfo.Title = title;
tocPage.TocInfo = tocInfo;
```

## Krok 4: Definujte prvky TOC

Definujte prvky (nebo nadpisy), které se zobrazí v obsahu. Tyto prvky mohou čtenářům pomoci při navigaci do konkrétních částí dokumentu.

```csharp
string[] titles = new string[4];
titles[0] = "First page";
titles[1] = "Second page";
titles[2] = "Third page";
titles[3] = "Fourth page";
```

## Krok 5: Vytvořte nadpisy obsahu

Vytvořte nadpisy pro první dva prvky v obsahu. Tyto nadpisy budou odkazovat na příslušné stránky.

```csharp
for (int i = 0; i < 2; i++)
{
    Aspose.Pdf.Heading heading2 = new Aspose.Pdf.Heading(1);
    TextSegment segment2 = new TextSegment();
    heading2.TocPage = tocPage;
    heading2.Segments.Add(segment2);

    heading2.DestinationPage = doc.Pages[i + 2];
    heading2.Top = doc.Pages[i + 2].Rect.Height;
    segment2.Text = titles[i];

    tocPage.Paragraphs.Add(heading2);
}
```

## Krok 6: Uložte soubor PDF s obsahem

Nakonec uložte aktualizovaný soubor PDF.

```csharp
dataDir = dataDir + "TOC_out.pdf";
doc.Save(dataDir);
```

## Potvrzující zpráva

Zobrazte potvrzovací zprávu, aby uživatel věděl, že proces je dokončen.

```csharp
Console.WriteLine("\nTOC added successfully to an existing PDF.\nFile saved at " + dataDir);
```

## Závěr

S Aspose.PDF pro .NET je přidání obsahu do PDF nejen snadné, ale také přizpůsobitelné. Ať už potřebujete vytvořit jednoduché navigační odkazy nebo složité struktury, tento nástroj vás pokryje. Takže až budete příště pracovat na zdlouhavém PDF, nezapomeňte přidat TOC pro profesionální dotek.

## FAQ

### Mohu upravit vzhled obsahu v Aspose.PDF?

Ano, můžete si plně přizpůsobit vzhled obsahu, včetně stylu písma, velikosti a zarovnání.

### Jak přidám podnadpisy do obsahu?

Můžete přidat podnadpisy úpravou`Heading` úroveň (např.`Heading(2)`).

### Je možné automaticky aktualizovat TOC, pokud se dokument změní?

Ne, obsah se neaktualizuje automaticky. Pokud se změní struktura dokumentu, budete jej muset znovu vytvořit.

### Mohu propojit položky TOC s externími dokumenty?

Ano, můžete použít hypertextové odkazy k propojení položek obsahu s externími soubory PDF nebo URL.

### Podporuje Aspose.PDF víceúrovňové TOC?

Ano, Aspose.PDF podporuje víceúrovňové TOC pro složité dokumenty s podsekcemi.
