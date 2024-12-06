---
title: Upravte soubory Zip pomocí Aspose.Zip pro .NET
linktitle: Upravte soubory ZIP
second_title: Aspose.Zip .NET API pro kompresi a archivaci souborů
description: Naučte se, jak efektivně extrahovat, odstraňovat a přidávat položky do souborů zip programově, a vylepšit tak možnosti manipulace se soubory.
type: docs
weight: 15
url: /cs/net/tutorials/zip/file-compress/modify-zip-files/
---
## Zavedení

Soubory ZIP jsou zásadní pro organizaci a kompresi dat, ale jak programově upravit jejich obsah? Řešení spočívá v Aspose.Zip for .NET, robustní knihovně, která zjednodušuje manipulaci se soubory zip pomocí C#. V tomto tutoriálu vás krok za krokem provedeme extrahováním, mazáním a přidáváním položek do souborů zip.

## Předpoklady

Než se ponoříme, ujistěte se, že máte následující:

1.  Aspose.Zip for .NET Library: Nainstalujte knihovnu do svého projektu. Můžete si jej stáhnout[zde](https://releases.aspose.com/zip/net/).
   
2.  Adresář dokumentů: Nastavte adresář pro ukládání souborů zip. Nahradit`"Your Document Directory"` v kódu s vaší skutečnou cestou.

## Importujte potřebné jmenné prostory

Začněte importem požadovaných jmenných prostorů:

```csharp
using Aspose.Zip;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
```

## Krok 1: Otevřete soubor vnější zip

Začněte otevřením hlavního souboru zip (vnější zip):

```csharp
string dataDir = "Your Data Directory";
using (Archive outer = new Archive(dataDir + "outer.zip"))
{
    // Pokračujte v identifikaci vnitřních vstupů zipu
}
```

## Krok 2: Identifikujte položky vnitřního zipu

Dále identifikujte a připravte se na odstranění všech vnitřních souborů zip:

```csharp
List<ArchiveEntry> entriesToDelete = new List<ArchiveEntry>();
List<string> namesToInsert = new List<string>();
List<MemoryStream> contentToInsert = new List<MemoryStream>();

foreach (ArchiveEntry entry in outer.Entries)
{
    if (entry.Name.EndsWith(".zip", StringComparison.InvariantCultureIgnoreCase))
    {
        entriesToDelete.Add(entry);
        
        using (MemoryStream innerCompressed = new MemoryStream())
        {
            entry.Open().CopyTo(innerCompressed);
            
            // Extrahujte vnitřní záznamy
            using (Archive inner = new Archive(innerCompressed))
            {
                foreach (ArchiveEntry ie in inner.Entries)
                {
                    namesToInsert.Add(ie.Name);
                    MemoryStream content = new MemoryStream();
                    ie.Open().CopyTo(content);
                    contentToInsert.Add(content);
                }
            }
        }
    }
}
```

## Krok 3: Odstraňte položky vnitřního archivu

Jakmile shromáždíte položky, které potřebujete, odstraňte vnitřní položky zip:

```csharp
foreach (ArchiveEntry e in entriesToDelete)
{
    outer.DeleteEntry(e);
}
```

## Krok 4: Přidejte upravené záznamy do vnějšího zipu

Nyní můžete nově extrahované položky přidat zpět do vnějšího souboru zip:

```csharp
for (int i = 0; i < namesToInsert.Count; i++)
{
    outer.CreateEntry(namesToInsert[i], contentToInsert[i]);
}
```

## Krok 5: Uložte upravený soubor ZIP

Nakonec uložte změny do nového souboru zip:

```csharp
outer.Save(dataDir + "flatten.zip");
```

## Závěr

Aspose.Zip for .NET poskytuje výkonný a přímočarý způsob, jak programově manipulovat se soubory zip. Tento výukový program se zabýval extrahováním, mazáním a přidáváním položek do souboru zip, což ilustrovalo všestrannost knihovny. Prozkoumejte různé scénáře a vylepšete své dovednosti při manipulaci se soubory!

## FAQ

### Mohu používat Aspose.Zip pro .NET s jinými programovacími jazyky?
Aspose.Zip je primárně určen pro .NET aplikace, ale Aspose nabízí podobné knihovny pro různé programovací jazyky.

### Je k dispozici bezplatná zkušební verze pro Aspose.Zip pro .NET?
 Ano, ke stažení je k dispozici bezplatná zkušební verze[zde](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Zip pro .NET?
 Navštivte[Fórum Aspose.Zip](https://forum.aspose.com/c/zip/37) za podporu a diskuze.

### Mohu si zakoupit dočasnou licenci pro Aspose.Zip pro .NET?
Ano, můžete získat dočasnou licenci[zde](https://purchase.conholdate.com/temporary-license/).

### Kde najdu dokumentaci k Aspose.Zip pro .NET?
 K dispozici je kompletní dokumentace[zde](https://reference.aspose.com/zip/net/).