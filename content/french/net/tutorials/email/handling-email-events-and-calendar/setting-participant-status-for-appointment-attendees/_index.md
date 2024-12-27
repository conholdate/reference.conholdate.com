---
title: Définition du statut de participant pour les participants au rendez-vous avec C#
linktitle: Définition du statut de participant pour les participants au rendez-vous avec C#
second_title: API de traitement des e-mails Aspose.Email .NET
description: Découvrez comment gérer le statut des participants aux rendez-vous à l'aide de C# et d'Aspose.Email pour .NET. Guide étape par étape avec code source.
type: docs
weight: 16
url: /fr/net/tutorials/email/handling-email-events-and-calendar/setting-participant-status-for-appointment-attendees/
---
## Introduction

Aspose.Email for .NET est une bibliothèque robuste et riche en fonctionnalités conçue pour rationaliser la gestion des e-mails dans les applications .NET. Ce guide fournit une procédure pas à pas pour créer et gérer des rendez-vous, ajouter des participants et définir des statuts de participants, garantissant ainsi une intégration efficace dans vos projets .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Une installation fonctionnelle de Visual Studio ou d’un IDE C# compatible.
- La dernière version de la bibliothèque Aspose.Email pour .NET.
- Connaissances de base du C# et de la programmation orientée objet.

 Pour l'installation de la bibliothèque, reportez-vous à la[page de téléchargement](https://releases.aspose.com/).

## Importer les espaces de noms requis

Pour commencer, incluez les espaces de noms nécessaires pour accéder aux fonctionnalités de gestion des rendez-vous et des composants de messagerie.

```csharp
using Aspose.Email;
using Aspose.Email.Calendar;
```

## Créer une instance de rendez-vous

Les rendez-vous dans Aspose.Email représentent des événements planifiés tels que des réunions ou des tâches. Voici comment en créer un :

```csharp
var appointment = new Appointment(
    "Conference Room 101", 
    DateTime.Now, 
    DateTime.Now.AddHours(1), 
    new MailAddress("organizer@example.com"),
    new MailAddressCollection { "attendee1@example.com", "attendee2@example.com" }
);
```

- Lieu : Spécifie où le rendez-vous aura lieu.
- StartTime et EndTime : Définissez la durée du rendez-vous.
- Organisateur et participants : définissez les participants et leurs rôles.

## Ajout de participants aux rendez-vous

Aspose.Email vous permet de gérer par programmation les participants avec leurs adresses e-mail et leurs statuts de participation.

```csharp
appointment.Attendees.Add(new MailAddress("john@example.com", "John Doe"));
appointment.Attendees.Add(new MailAddress("jane@example.com", "Jane Smith"));
```

## Gestion des statuts des participants

 Le`ParticipantStatus` La propriété permet de déterminer si un participant a accepté, refusé ou accepté provisoirement une invitation à un rendez-vous. Utilisez les valeurs d'énumération suivantes :

- Accepté
- Refusé
- Provisoire

Exemple:

```csharp
appointment.Attendees[0].ParticipantStatus = AppointmentParticipantStatus.Accepted;
appointment.Attendees[1].ParticipantStatus = AppointmentParticipantStatus.Declined;
```

## Envoi de rendez-vous sous forme d'invitations à des réunions

Une fois le rendez-vous préparé, vous pouvez l'envoyer sous forme d'email d'invitation :

```csharp
var msg = new MailMessage();
msg.From = "organizer@example.com";
msg.To = new MailAddressCollection { "john@example.com", "jane@example.com" };
msg.Subject = "Team Meeting";
msg.AlternateViews.Add(appointment.RequestApointment());

var client = new SmtpClient("smtp.example.com", 587, "username", "password");
client.Send(msg);
```

## Conclusion

Aspose.Email pour .NET simplifie la gestion des rendez-vous dans les applications .NET, en fournissant des outils permettant de créer, de personnaliser et de gérer efficacement les événements planifiés. Grâce à son API intuitive, vous pouvez rationaliser les flux de communication et garantir une intégration transparente.

## FAQ

### Qu'est-ce qu'Aspose.Email pour .NET ?

Aspose.Email pour .NET est une bibliothèque complète pour la gestion des messages électroniques, des rendez-vous et d'autres fonctionnalités associées dans les applications .NET.

### Puis-je personnaliser les propriétés du rendez-vous ?

Oui, les propriétés telles que l’emplacement, l’heure de début et les participants peuvent être entièrement personnalisées.

### La bibliothèque prend-elle en charge les rendez-vous récurrents ?

Oui, Aspose.Email pour .NET prend en charge les rendez-vous récurrents à l’aide de son API de modèle de récurrence.

### Où puis-je obtenir de l'aide pour Aspose.Email pour .NET ?

 Vous pouvez accéder à une documentation détaillée et au support communautaire sur le[page d'assistance](https://forum.aspose.com/c/email/11).