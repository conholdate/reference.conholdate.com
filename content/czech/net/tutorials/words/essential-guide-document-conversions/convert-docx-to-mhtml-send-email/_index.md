---
title: Převést DOCX na MHTML a odeslat e-mail pomocí Aspose.Words pro .NET
linktitle: Převést DOCX na MHTML a odeslat e-mail pomocí Aspose.Words pro .NET
second_title: Aspose.Words API pro zpracování dokumentů
description: Tento komplexní průvodce poskytuje podrobný návod na převod dokumentů DOCX do formátu MHTML a jejich odesílání e-mailem pomocí knihoven Aspose.Words a Aspose.Email v .NET.
type: docs
weight: 10
url: /cs/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Zavedení

V dnešním digitálním prostředí je převod dokumentů mezi formáty a jejich zasílání e-mailem běžným úkolem. Tato příručka vás provede převodem souboru DOCX do formátu MHTML a jeho odesláním e-mailem pomocí výkonných knihoven Aspose.Words a Aspose.Email pro .NET. Jasně rozepíšeme každý krok, abyste je mohli snadno sledovat. Začněme!

## Předpoklady

Než se ponoříte do procesu, ujistěte se, že máte následující nastavení:

1.  Aspose.Words for .NET: Stáhněte a nainstalujte knihovnu z[Aspose stránku vydání](https://releases.aspose.com/words/net/).
2.  Aspose.Email pro .NET: Stáhněte a nainstalujte tuto knihovnu z[Aspose stránku vydání](https://releases.aspose.com/email/net/).
3. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
4. Server SMTP: K odesílání e-mailů budete potřebovat přístup k serveru SMTP.

## Import nezbytných jmenných prostorů

Chcete-li ve svém projektu používat Aspose.Words a Aspose.Email, musíte importovat požadované jmenné prostory. Přidejte následující pomocí direktiv v horní části souboru C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Krok 1: Vložte dokument DOCX

 Začněte načtením dokumentu DOCX, který chcete převést. Použijte`Document` třídy z Aspose.Words, abyste toho dosáhli.

```csharp
// Zadejte cestu k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Krok 2: Uložte dokument jako MHTML

 Dále převeďte načtený dokument do formátu MHTML. To se provádí pomocí`Save` metoda`Document`třída.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Pro čtení nastavte polohu streamu na začátek.
    stream.Position = 0;
}
```

## Krok 3: Vytvořte e-mailovou zprávu

Nyní vytvořte e-mailovou zprávu ze streamu MHTML pomocí Aspose.Email. Budete využívat`MailMessage` třídy pro tento účel.

```csharp
// Načtěte proud MHTML do e-mailové zprávy Aspose.Email MIME.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Krok 4: Odešlete e-mail

 Nakonec odešlete e-mail pomocí klienta SMTP. Nakonfigurujte klienta SMTP pomocí podrobností o vašem serveru a použijte jej`Send` způsob odeslání zprávy.

```csharp
// Nakonfigurujte a odešlete zprávu pomocí Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Závěr

Gratuluji! Úspěšně jste převedli dokument DOCX do MHTML a odeslali jej e-mailem pomocí Aspose.Words a Aspose.Email pro .NET. Tento proces zahrnuje načtení dokumentu, jeho převod do MHTML, vytvoření e-mailové zprávy a její odeslání prostřednictvím klienta SMTP. Pomocí těchto kroků můžete ve svých aplikacích bezproblémově automatizovat převod a zasílání dokumentů e-mailem.

## FAQ

### Mohu tuto metodu použít k převodu jiných formátů dokumentů?
Absolutně! Aspose.Words podporuje širokou škálu formátů, což vám umožňuje převádět DOC, DOCX, RTF a další do MHTML.

### Jak mohu k e-mailu přidat přílohy?
 Přílohy můžete snadno přidávat pomocí`Attachments` vlastnictvím`MailMessage`třída.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words je kompatibilní s .NET Core, takže je vhodný pro použití v aplikacích .NET Core.

### Potřebuji licenci pro Aspose.Words a Aspose.Email?
 Ano, obě knihovny vyžadují licenci. Dočasnou licenci pro zkušební účely můžete získat od[Aspose nákupní stránku](https://purchase.conholdate.com/temporary-license/).

### Kde najdu další dokumentaci?
 Pro podrobnou dokumentaci se podívejte na Aspose.Words[zde](https://reference.aspose.com/words/net/) a Aspose.Email[zde](https://reference.aspose.com/email/net/).