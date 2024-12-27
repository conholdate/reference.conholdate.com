---
title: Converteer DOCX naar MHTML en verstuur e-mail met Aspose.Words voor .NET
linktitle: Converteer DOCX naar MHTML en verstuur e-mail met Aspose.Words voor .NET
second_title: Aspose.Words API voor documentverwerking
description: Deze uitgebreide handleiding biedt een stapsgewijze zelfstudie voor het converteren van DOCX-documenten naar MHTML-indeling en het e-mailen ervan met behulp van de bibliotheken Aspose.Words en Aspose.Email in .NET.
type: docs
weight: 10
url: /nl/net/tutorials/words/essential-guide-document-conversions/convert-docx-to-mhtml-send-email/
---
## Invoering

In het digitale landschap van vandaag de dag is het converteren van documenten tussen formaten en het e-mailen ervan een veelvoorkomende taak. Deze gids leidt u door het converteren van een DOCX-bestand naar MHTML-formaat en het verzenden ervan via e-mail met behulp van de krachtige Aspose.Words- en Aspose.Email-bibliotheken voor .NET. We zullen elke stap duidelijk uitleggen, zodat u het gemakkelijk kunt volgen. Laten we beginnen!

## Vereisten

Voordat u aan het proces begint, moet u ervoor zorgen dat u het volgende hebt ingesteld:

1.  Aspose.Words voor .NET: Download en installeer de bibliotheek van de[Aspose releases pagina](https://releases.aspose.com/words/net/).
2.  Aspose.Email voor .NET: Download en installeer deze bibliotheek van de[Aspose releases pagina](https://releases.aspose.com/email/net/).
3. .NET Framework: Zorg ervoor dat .NET Framework op uw computer is geïnstalleerd.
4. SMTP-server: U hebt toegang tot een SMTP-server nodig om e-mails te kunnen verzenden.

## Noodzakelijke naamruimten importeren

Om Aspose.Words en Aspose.Email in uw project te gebruiken, moet u de vereiste naamruimten importeren. Voeg het volgende toe met behulp van richtlijnen boven aan uw C#-bestand:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using Aspose.Email;
using Aspose.Email.Mime;
using Aspose.Email.Clients.Smtp;
```

## Stap 1: Laad het DOCX-document

 Begin met het laden van het DOCX-document dat u wilt converteren. Gebruik de`Document` klasse van Aspose.Woorden om dit te bereiken.

```csharp
// Geef het pad naar uw documentenmap op.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

## Stap 2: Sla het document op als MHTML

 Converteer vervolgens het geladen document naar MHTML-formaat. Dit doet u met behulp van de`Save` methode van de`Document` klas.

```csharp
using (Stream stream = new MemoryStream())
{
    doc.Save(stream, SaveFormat.Mhtml);
    // Zet de streampositie terug naar het begin om te kunnen lezen.
    stream.Position = 0;
}
```

## Stap 3: Maak een e-mailbericht

Maak nu een e-mailbericht van de MHTML-stream met behulp van Aspose.Email. U gebruikt de`MailMessage` klasse voor dit doel.

```csharp
// Laad de MHTML-stream in een Aspose.Email MIME-e-mailbericht.
MailMessage message = MailMessage.Load(stream, new MhtmlLoadOptions());
message.From = "your_from@email.com";
message.To = "your_to@email.com";
message.Subject = "Aspose.Words + Aspose.Email MHTML Test Message";
```

## Stap 4: Verstuur de e-mail

 Verstuur ten slotte de e-mail met een SMTP-client. Configureer de SMTP-client met uw servergegevens en gebruik de`Send` Methode om het bericht te verzenden.

```csharp
// Configureer en verstuur het bericht met Aspose.Email.
using (SmtpClient client = new SmtpClient())
{
    client.Host = "your_smtp.com";
    client.Send(message);
}
```

## Conclusie

Gefeliciteerd! U hebt met succes een DOCX-document naar MHTML geconverteerd en via e-mail verzonden met Aspose.Words en Aspose.Email voor .NET. Dit proces omvat het laden van het document, het converteren naar MHTML, het maken van een e-mailbericht en het verzenden ervan via een SMTP-client. Met deze stappen kunt u de conversie en het e-mailen van documenten naadloos automatiseren in uw toepassingen.

## Veelgestelde vragen

### Kan ik deze methode gebruiken om andere documentformaten te converteren?
Absoluut! Aspose.Words ondersteunt een breed scala aan formaten, zodat u DOC, DOCX, RTF en meer naar MHTML kunt converteren.

### Hoe kan ik bijlagen aan de e-mail toevoegen?
 U kunt eenvoudig bijlagen toevoegen met behulp van de`Attachments` eigendom van de`MailMessage` klas.

### Is Aspose.Words compatibel met .NET Core?
Ja, Aspose.Words is compatibel met .NET Core en is daardoor geschikt voor gebruik in .NET Core-toepassingen.

### Heb ik een licentie nodig voor Aspose.Words en Aspose.Email?
 Ja, beide bibliotheken vereisen een licentie. U kunt een tijdelijke licentie voor evaluatiedoeleinden verkrijgen bij de[Aspose aankooppagina](https://purchase.conholdate.com/temporary-license/).

### Waar kan ik meer documentatie vinden?
 Voor gedetailleerde documentatie, bekijk Aspose.Words[hier](https://reference.aspose.com/words/net/) en Aspose.E-mail[hier](https://reference.aspose.com/email/net/).