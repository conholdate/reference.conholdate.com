---
title: Konvertera DOCX till MHTML och skicka e-post med Aspose.Words för .NET
linktitle: Konvertera DOCX till MHTML och skicka e-post med Aspose.Words för .NET
second_title: Aspose.Words Document Processing API
description: Den här omfattande guiden ger en steg-för-steg handledning om hur du konverterar DOCX-dokument till MHTML-format och e-postar dem med Aspose.Words och Aspose.Email-bibliotek i .NET.
type: docs
weight: 10
url: /sv/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Introduktion

I dagens digitala landskap är det en vanlig uppgift att konvertera dokument mellan format och e-posta dem. Den här guiden leder dig genom att konvertera en DOCX-fil till MHTML-format och skicka den via e-post med hjälp av de kraftfulla Aspose.Words- och Aspose.Email-biblioteken för .NET. Vi kommer att dela upp varje steg tydligt, så att du kan följa med med lätthet. Låt oss komma igång!

## Förutsättningar

Innan du går in i processen, se till att du har följande inställning:

1.  Aspose.Words för .NET: Ladda ner och installera biblioteket från[Aspose releaser sida](https://releases.aspose.com/words/net/).
2.  Aspose.Email för .NET: Ladda ner och installera det här biblioteket från[Aspose releaser sida](https://releases.aspose.com/email/net/).
3. .NET Framework: Se till att du har .NET Framework installerat på din dator.
4. SMTP-server: Du behöver tillgång till en SMTP-server för att skicka e-post.

## Importera nödvändiga namnområden

För att använda Aspose.Words och Aspose.Email i ditt projekt måste du importera de nödvändiga namnrymden. Lägg till följande med hjälp av direktiv överst i din C#-fil:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Steg 1: Ladda DOCX-dokumentet

 Börja med att ladda DOCX-dokumentet du vill konvertera. Använd`Document` klass från Aspose.Words för att åstadkomma detta.

```csharp
// Ange sökvägen till din dokumentkatalog.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Steg 2: Spara dokumentet som MHTML

 Konvertera sedan det laddade dokumentet till MHTML-format. Detta görs med hjälp av`Save` metod för`Document`klass.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Återställ strömningspositionen till början för läsning.
    stream.Position = 0;
}
```

## Steg 3: Skapa ett e-postmeddelande

Skapa nu ett e-postmeddelande från MHTML-strömmen med Aspose.Email. Du kommer att använda`MailMessage` klass för detta ändamål.

```csharp
// Ladda MHTML-strömmen till ett Aspose.Email MIME-e-postmeddelande.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Steg 4: Skicka e-postmeddelandet

 Slutligen, skicka e-postmeddelandet med en SMTP-klient. Konfigurera SMTP-klienten med dina serverdetaljer och använd`Send` metod för att skicka meddelandet.

```csharp
// Konfigurera och skicka meddelandet med Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Slutsats

Grattis! Du har framgångsrikt konverterat ett DOCX-dokument till MHTML och skickat det via e-post med Aspose.Words och Aspose.Email för .NET. Denna process involverar att ladda dokumentet, konvertera det till MHTML, skapa ett e-postmeddelande och skicka det via en SMTP-klient. Med dessa steg kan du automatisera konverteringen och e-posten av dokument sömlöst i dina applikationer.

## FAQ's

### Kan jag använda den här metoden för att konvertera andra dokumentformat?
Absolut! Aspose.Words stöder ett brett utbud av format, så att du kan konvertera DOC, DOCX, RTF och mer till MHTML.

### Hur kan jag lägga till bilagor till e-postmeddelandet?
 Du kan enkelt lägga till bilagor med hjälp av`Attachments` egendom av`MailMessage`klass.

### Är Aspose.Words kompatibelt med .NET Core?
Ja, Aspose.Words är kompatibelt med .NET Core, vilket gör det lämpligt för användning i .NET Core-applikationer.

### Behöver jag en licens för Aspose.Words och Aspose.Email?
 Ja, båda biblioteken kräver en licens. Du kan få en tillfällig licens för utvärderingsändamål från[Aspose köpsida](https://purchase.conholdate.com/temporary-license/).

### Var kan jag hitta mer dokumentation?
 För detaljerad dokumentation, kolla in Aspose.Words[här](https://reference.aspose.com/words/net/) och Aspose.Email[här](https://reference.aspose.com/email/net/).