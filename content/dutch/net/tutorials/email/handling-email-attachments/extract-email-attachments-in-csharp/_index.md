---
title: E-mailbijlagen extraheren in C# - Aspose.Email-zelfstudie
linktitle: E-mailbijlagen extraheren in C# - Aspose.Email-zelfstudie
second_title: Aspose.Email .NET E-mailverwerkings-API
description: Leer hoe u e-mailbijlagen in C# kunt extraheren met Aspose.Email voor .NET. Stapsgewijze handleiding met voorbeelden voor PDF's, afbeeldingen en meer.
type: docs
weight: 14
url: /nl/net/tutorials/email/handling-email-attachments/extract-email-attachments-in-csharp/
---
## Invoering

Heb je ooit handmatig e-mailbijlagen gedownload, één voor één? Het is niet alleen tijdrovend, maar ook foutgevoelig. Gelukkig biedt Aspose.Email voor .NET een krachtige en efficiënte manier om deze taak te automatiseren. Of je nu met PDF's, afbeeldingen of een ander bestandstype werkt, je kunt bijlagen moeiteloos extraheren met C#.

In deze gids leiden we je door een complete tutorial, beginnend bij de vereisten tot een volledig werkend voorbeeld. Klaar om uren aan handmatig werk te besparen? Laten we erin duiken!

## Vereisten

Voordat u begint met coderen, moet u ervoor zorgen dat u het volgende heeft:

- Visual Studio op uw computer geïnstalleerd.
-  Aspose.Email voor .NET-bibliotheek. U kunt[download het hier](https://releases.aspose.com/email/net/) of installeer het via NuGet.
- Een geldig e-mailaccount (IMAP/POP3 ondersteund).
- Basiskennis van C#-programmering.

 Als u nieuw bent bij Aspose.Email, overweeg dan om een[gratis proefperiode](https://releases.aspose.com/) of een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/) om alle functies te ontgrendelen.

## Pakketten importeren

Voordat u in de code duikt, moet u ervoor zorgen dat u de benodigde namespaces hebt geïmporteerd. Voeg het volgende toe bovenaan uw C#-bestand:

```csharp
using Aspose.Email;
using Aspose.Email.Clients.Imap;
using Aspose.Email.Clients.Pop3;
```

Laten we het proces opsplitsen in verteerbare stappen. Volg elke stap zorgvuldig om een soepele uitvoering te garanderen.


## Stap 1: Stel uw IMAP-client in

De eerste stap is om verbinding te maken met uw e-mailserver met behulp van het IMAP-protocol. IMAP stelt ons in staat om e-mailberichten van de server te openen en op te halen.

```csharp
ImapClient client = new ImapClient("imap.example.com", "username", "password");
client.SelectFolder(ImapFolderInfo.InBox);
```

-  Vervangen`imap.example.com` met het IMAP-serveradres van uw e-mailprovider (bijv.`imap.gmail.com` voor Gmail).
-  Gebruik uw echte e-mailadres`username` En`password`.
- `SelectFolder(ImapFolderInfo.InBox)`geeft aan dat we met de inbox willen werken.


## Stap 2: E-mails ophalen uit de inbox

Zodra u bent verbonden, moet u e-mailberichten uit de inbox ophalen. Aspose.Email biedt een eenvoudige methode om alle berichten weer te geven.

```csharp
ImapMessageInfoCollection messages = client.ListMessages();
```

- `ListMessages()` haalt metagegevens op voor alle e-mails in de inbox.
-  De`ImapMessageInfoCollection` Het object bevat details zoals de afzender, het onderwerp en unieke ID's.


## Stap 3: Haal elk e-mailbericht op

Om toegang te krijgen tot de inhoud en bijlagen, moet u elke e-mail ophalen met behulp van de unieke ID.


```csharp
foreach (ImapMessageInfo messageInfo in messages)
{
    MailMessage message = client.FetchMessage(messageInfo.UniqueId);
}
```

-  De`foreach` lus doorloopt alle berichten.
- `FetchMessage()` haalt de werkelijke e-mailinhoud op voor een bepaalde bericht-ID.


## Stap 4: Loop door bijlagen

 Nu u de e-mailinhoud hebt, is het tijd om bijlagen te extraheren. Elk`MailMessage` object bevat een verzameling bijlagen.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    Console.WriteLine($"Attachment Name: {attachment.Name}");
}
```

-  De`Attachments` eigenschap geeft een overzicht van alle bijlagen in de e-mail.
-  Gebruik`attachment.Name` om de bestandsnaam te verkrijgen.


## Stap 5: Bijlagen op schijf opslaan

Sla ten slotte de bijlagen op uw lokale machine op. U kunt bestanden filteren op type, grootte of andere criteria.

```csharp
foreach (Attachment attachment in message.Attachments)
{
    string filePath = Path.Combine("C:\\Attachments", attachment.Name);
    using (var stream = new FileStream(filePath, FileMode.Create))
    {
        attachment.Save(stream);
    }
}
```

-  Vervangen`"C:\\Attachments"`met het gewenste mappad.
-  De`attachment.Save()` methode schrijft het bestand naar schijf.


## Stap 6: Bijlagen verwerken op type

Als u bijlagen op basis van het type anders wilt verwerken (bijvoorbeeld PDF versus JPEG), maakt Aspose.Email het u gemakkelijk.

```csharp
if (attachment.ContentType.MediaType == "application/pdf")
{
    Console.WriteLine("Processing PDF...");
}
else if (attachment.ContentType.MediaType == "image/jpeg")
{
    Console.WriteLine("Processing JPEG...");
}
```

- `ContentType.MediaType` identificeert het bestandstype (bijv.`application/pdf` voor PDF's,`image/jpeg` voor afbeeldingen).
- Voeg indien nodig aangepaste logica toe voor verschillende bestandstypen.


## Conclusie

En daar heb je het! Het extraheren van bijlagen uit e-mails is niet langer een vervelende taak. Met Aspose.Email voor .NET kun je dit proces automatiseren in slechts een paar regels code. Van het instellen van de IMAP-client tot het lokaal opslaan van bijlagen, deze gids heeft alles behandeld wat je nodig hebt om te beginnen. 

 Waarom zou je dan nog wachten?[Download Aspose.E-mail](https://releases.aspose.com/email/net/) en begin vandaag nog met het stroomlijnen van uw e-mailworkflows!


## Veelgestelde vragen

### Kan ik deze code gebruiken met Gmail of Outlook?
 Ja! Vervangen`imap.example.com` met Gmail's (`imap.gmail.com`) of Outlook's (`outlook.office365.com`) IMAP-serveradres.

### Is Aspose.Email gratis te gebruiken?
 Aspose.Email vereist een licentie voor volledige functies. U kunt een[gratis proefperiode](https://releases.aspose.com/) of een[tijdelijke licentie](https://purchase.aspose.com/temporary-license/).

### Hoe kan ik de beveiliging van mijn wachtwoorden regelen?
Overweeg om omgevingsvariabelen of veilige opslag van inloggegevens te gebruiken in plaats van het hardcoderen van wachtwoorden.

### Kan ik bijlagen uit verzonden items halen?
 Ja, gebruik gewoon`SelectFolder(ImapFolderInfo.Sent)` in plaats van de inbox.

### Ondersteunt Aspose.Email POP3?
Absoluut! Naast IMAP ondersteunt het ook POP3 en SMTP.