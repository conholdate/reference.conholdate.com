---
title: Instellen van de deelnemersstatus voor deelnemers aan afspraken met C#
linktitle: Instellen van de deelnemersstatus voor deelnemers aan afspraken met C#
second_title: Aspose.Email .NET E-mailverwerkings-API
description: Leer hoe u de status van deelnemers aan afspraken kunt beheren met C# en Aspose.Email voor .NET. Stapsgewijze handleiding met broncode.
type: docs
weight: 16
url: /nl/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Invoering

Aspose.Email voor .NET is een robuuste en feature-rijke bibliotheek die is ontworpen om e-mailverwerking in .NET-toepassingen te stroomlijnen. Deze gids biedt een stapsgewijze walkthrough van het maken en beheren van afspraken, het toevoegen van deelnemers en het instellen van deelnemersstatussen, wat zorgt voor efficiënte integratie in uw .NET-projecten.

## Vereisten

Voordat u begint, moet u ervoor zorgen dat u over het volgende beschikt:

- Een werkende installatie van Visual Studio of een compatibele C# IDE.
- De nieuwste versie van de Aspose.Email voor .NET-bibliotheek.
- Basiskennis van C# en objectgeoriënteerd programmeren.

 Voor bibliotheekinstallatie, zie de[downloadpagina](https://releases.aspose.com/).

## Vereiste naamruimten importeren

Om te beginnen voegt u de benodigde naamruimten toe om toegang te krijgen tot de functionaliteiten voor het beheren van afspraken en e-mailcomponenten.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Een afspraakinstantie maken

Afspraken in Aspose.Email vertegenwoordigen geplande gebeurtenissen zoals vergaderingen of taken. Zo maakt u er een:

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Locatie: Geeft aan waar de afspraak zal plaatsvinden.
- StartTime en EndTime: Definieer de duur van de afspraak.
- Organisatoren en deelnemers: Definieer deelnemers en hun rollen.

## Deelnemers toevoegen aan afspraken

Met Aspose.Email kunt u deelnemers programmatisch beheren met hun e-mailadressen en deelnamestatussen.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Deelnemersstatussen beheren

 De`ParticipantStatus` eigenschap helpt bepalen of een deelnemer een afspraakuitnodiging heeft geaccepteerd, afgewezen of voorlopig heeft geaccepteerd. Gebruik de volgende opsommingswaarden:

- Geaccepteerd
- Afgewezen
- Voorlopig

Voorbeeld:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Afspraken verzenden als uitnodigingen voor vergaderingen

Zodra de afspraak is voorbereid, kunt u deze als uitnodigingsmail versturen:

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Conclusie

Aspose.Email voor .NET vereenvoudigt het beheer van afspraken in .NET-applicaties en biedt tools voor het efficiënt maken, aanpassen en beheren van geplande evenementen. Met de intuïtieve API kunt u communicatieworkflows stroomlijnen en zorgen voor naadloze integratie.

## Veelgestelde vragen

### Wat is Aspose.Email voor .NET?

Aspose.Email voor .NET is een uitgebreide bibliotheek voor het verwerken van e-mailberichten, afspraken en andere gerelateerde functionaliteiten in .NET-toepassingen.

### Kan ik de eigenschappen van afspraken aanpassen?

Ja, eigenschappen zoals locatie, starttijd en deelnemers kunnen volledig worden aangepast.

### Ondersteunt de bibliotheek terugkerende afspraken?

Ja, Aspose.Email voor .NET ondersteunt terugkerende afspraken via de API voor terugkeerpatronen.

### Waar kan ik ondersteuning krijgen voor Aspose.Email voor .NET?

 Gedetailleerde documentatie en community-ondersteuning vindt u op de[ondersteuningspagina](https://forum.aspose.com/c/email/11).