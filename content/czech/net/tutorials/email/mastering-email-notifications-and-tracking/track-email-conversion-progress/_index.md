---
title: Sledujte průběh konverze e-mailu pomocí Aspose.Email pro .NET
linktitle: Sledujte průběh konverze e-mailu pomocí Aspose.Email pro .NET
second_title: Aspose.Email .NET Email Processing API
description: Naučte se krok za krokem sledovat průběh konverze e-mailu v C# pomocí Aspose.Email pro .NET. Zvyšte efektivitu svého projektu pomocí tohoto podrobného návodu.
type: docs
weight: 12
url: /cs/net/tutorials/email/mastering-email-notifications-and-tracking/track-email-conversion-progress/
---
## Zavedení

Efektivní správa e-mailových dokumentů často zahrnuje sledování průběhu jejich převodu. Aspose.Email for .NET poskytuje robustní nástroje k dosažení tohoto cíle a umožňuje vývojářům bezproblémově zpracovávat e-mailové operace. Tento výukový program se ponoří do toho, jak můžete sledovat průběh převodu e-mailových dokumentů v C#, a pro snazší pochopení celý proces rozebírá krok za krokem.  

## Předpoklady  

Než se vrhneme na tutoriál, ujistěte se, že máte vše nastaveno:  

1.  Aspose.Email pro .NET: Stáhněte a nainstalujte[Aspose.Email pro .NET](https://releases.aspose.com/email/net/) knihovna.  
2. Vývojové prostředí: Nainstalujte Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.  
3. .NET Framework: Ujistěte se, že je nainstalováno rozhraní .NET Framework 4.5 nebo novější.  
4.  Dočasná licence: Zvažte získání a[dočasná licence](https://purchase.aspose.com/temporary-license/) prozkoumat všechny funkce Aspose.Email.  
5.  Ukázkový e-mailový soubor: Připravte si`.eml` soubor (např.`test.eml`) použít jako vzorek.  

## Importujte balíčky  

Chcete-li ve svém projektu použít Aspose.Email, budete muset importovat požadované jmenné prostory. Přidejte následující pomocí příkazů na začátek souboru:  

```csharp
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.SaveOptions;
using System;
using System.IO;
```

## Krok 1: Nastavte svůj projekt  

Začněte vytvořením nové konzolové aplikace C# v sadě Visual Studio. To bude sloužit jako základ pro implementaci sledování konverzí e-mailových dokumentů.  
  
1. Otevřete Visual Studio a vytvořte nový projekt aplikace konzoly.  
2. Nainstalujte balíček Aspose.Email NuGet:  
```sh
Install-Package Aspose.Email
```  
3.  Přidejte`.eml` soubor do adresáře vašeho projektu.  

## Krok 2: Načtěte soubor e-mailu  

 Nyní načtěte e-mailový soubor do a`MailMessage` objekt. Toto je první krok v práci s e-mailovými daty.  
 
```csharp
string dataDir = "Your Document Directory";
var fileName = dataDir + "test.eml";
MailMessage msg = MailMessage.Load(fileName);
```
 
- `dataDir`: Určuje adresář, kde je umístěn váš e-mailový soubor.  
- `MailMessage.Load` : Čte`.eml` soubor a připraví jej pro další operace.  

## Krok 3: Inicializujte Memory Stream  

 Dále vytvořte a`MemoryStream` objekt k dočasnému uložení převedených e-mailových dat.  
 
```csharp
MemoryStream ms = new MemoryStream();
```

 A`MemoryStream` se zde používá ke správě výstupu procesu převodu bez ukládání dat přímo na disk.  

## Krok 4: Definujte možnosti převodu  

 Nastavte`EmlSaveOptions` s vlastním obslužným nástrojem pro sledování průběhu konverze.  
 
```csharp
EmlSaveOptions opt = new EmlSaveOptions(MailMessageSaveType.EmlFormat);
opt.CustomProgressHandler = new ConversionProgressEventHandler(ShowEmlConversionProgress);
```
  
- `MailMessageSaveType.EmlFormat`: Určuje výstupní formát.  
- `CustomProgressHandler`: Přiřadí funkci vlastního obslužného programu pro sledování průběhu.  

## Krok 5: Uložte e-mail do Memory Stream  

Uložit`MailMessage` objekt pomocí zadaných voleb, umožňujících funkci sledování průběhu.  
 
```csharp
msg.Save(ms, opt);
```
 
Tento krok zahájí proces převodu e-mailu a odešle aktualizace do obslužné rutiny průběhu.  

## Krok 6: Implementujte nástroj Progress Handler  

 Definujte`ShowEmlConversionProgress` způsob zpracování aktualizací průběhu a jejich zobrazení v konzole.  
 
```csharp
private static void ShowEmlConversionProgress(ProgressEventHandlerInfo info)
{
    int total;
    int saved;

    switch (info.EventType)
    {
        case ProgressEventType.MimeStructureCreated:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimeStructureCreated - TotalMimePartCount: {total}");
            Console.WriteLine($"MimeStructureCreated - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.MimePartSaved:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"MimePartSaved - TotalMimePartCount: {total}");
            Console.WriteLine($"MimePartSaved - SavedMimePartCount: {saved}");
            break;

        case ProgressEventType.SavedToStream:
            total = info.TotalMimePartCount;
            saved = info.SavedMimePartCount;
            Console.WriteLine($"SavedToStream - TotalMimePartCount: {total}");
            Console.WriteLine($"SavedToStream - SavedMimePartCount: {saved}");
            break;
    }
}
```
 
- `ProgressEventHandlerInfo`: Poskytuje podrobnosti o procesu převodu.  
-  Případy přepínačů: Zvládněte různé fáze převodu:`MimeStructureCreated`, `MimePartSaved` a`SavedToStream`.  

### co očekávat?  
Jak převod postupuje, uvidíte na konzoli vytištěné podrobné aktualizace, například:  
```plaintext
MimeStructureCreated - TotalMimePartCount: 10  
MimeStructureCreated - SavedMimePartCount: 3  
MimePartSaved - TotalMimePartCount: 10  
MimePartSaved - SavedMimePartCount: 5  
```

## Závěr  

Sledování průběhu převodu e-mailových dokumentů v C# nebylo nikdy jednodušší díky Aspose.Email pro .NET. Sledováním tohoto kurzu jste se naučili, jak načíst e-mailový soubor, nastavit obslužný program průběhu a uložit data e-mailu a zároveň sledovat celý proces. Tato funkce zajišťuje, že během operací s e-mailovými dokumenty zůstanete informováni a budete mít kontrolu.  

## FAQ  

###  Mohu tento kód použít pro jiné formáty než`.eml`?  
 Ano, upravit`MailMessageSaveType`aby vyhovovaly jiným formátům, jako je MSG nebo MHTML.  

### Jak zpracuji velké e-mailové soubory?  
 Zvažte použití a`FileStream` místo a`MemoryStream` pro lepší výkon s velkými soubory.  

### Co je to dočasná licence a jak ji získám?  
 Dočasná licence vám umožňuje zdarma otestovat všechny funkce knihovny. Získejte to[zde](https://purchase.aspose.com/temporary-license/).  

### Mohu tento kód integrovat do webové aplikace?  
Ano, kód je kompatibilní s webovými aplikacemi využívajícími ASP.NET nebo podobné frameworky.  

### Kde najdu další zdroje?  
 Podívejte se na[dokumentace](https://reference.aspose.com/email/net/) nebo navštivte[fórum podpory](https://forum.aspose.com/c/email/12/) o pomoc.  